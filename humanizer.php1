// humanizer.php - Free Text Humanizer API
header("Access-Control-Allow-Origin: *");
header("Content-Type: application/json");

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $data = json_decode(file_get_contents("php://input"), true);
    if (!isset($data['text'])) {
        echo json_encode(["error" => "No text provided"]);
        exit;
    }
    
    $text = $data['text'];
    $humanizedText = humanizeText($text);
    echo json_encode(["humanized_text" => $humanizedText]);
} else {
    echo json_encode(["error" => "Invalid request method"]);
}

function humanizeText($text) {
    $replacements = [
        "moreover" => "also",
        "in addition to" => "besides",
        "thus" => "so",
        "therefore" => "so",
        "utilize" => "use",
        "subsequently" => "later",
        "in order to" => "to",
        "assist" => "help",
        "demonstrate" => "show",
        "elucidate" => "explain"
    ];
    
    foreach ($replacements as $robotic => $human) {
        $text = preg_replace("/\b" . preg_quote($robotic, '/') . "\b/i", $human, $text);
    }
    return $text;
}
