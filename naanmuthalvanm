<?php
$data = json_decode(file_get_contents("php://input"), true);
$image_data = $data['image'];

$image_data = str_replace('data:image/png;base64,', '', $image_data);
$image_data = base64_decode($image_data);
$file_path = 'temp.png';
file_put_contents($file_path, $image_data);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, "http://127.0.0.1:5000/predict");
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, ['image' => new CURLFile($file_path)]);
$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>
