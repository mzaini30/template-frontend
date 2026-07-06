VARIABLE

$whatsapp = bZYMoXDsIyjUVgognpKrdYylgwKzAOCHgHFjbdLeOJwosdtjAv000
$pakasir = bayar

SKILLS

- Selalu gunakan skill caveman
- Selalu cek skill apa yang cocok dan otomatis install dengan: skills add [nama skillnya] -y

TIMEZONE

- Asia/Makassar (UTC + 8)

CHUNKING

- Pecah-pecah filenya supaya reusable dan mudah diolah AI

FRONTEND

- Gunakan bahasa Indonesia
- Menggunakan SvelteKit
- Tampilan hanya mobile. Ketika dibuka di desktop, max width 600px
- Untuk install dependencies, jangan gunakan npm. Hanya gunakan pnpm
- Setiap alert, ganti dengan toast
- Setiap interaksi, kasih bunyi beep yang cocok, supaya rame aja
- Untuk tampilan, gunakan file DESIGN.md
- Untuk kompresi gambar, menggunakan bantuan i0.wp.com. Untuk docsnya, bisa ditemukan di ./knowledge/i0.txt

PEMBAYARAN

- Untuk pembayaran, gunakan Pakasir
- Docsnya ada di knowledge/pakasir.txt
- Slug Pakasir yang digunakan adalah $pakasir

WHATSAPP

- Untuk komunikasi dengan WhatsApp menggunakan Sidobe yang docsnya berada di knowledge/sidobe.txt
- API keynya adalah $whatsapp
- Untuk nomor WhatsApp berformat 081234567890 akan secara otomatis diubah menjadi format +6281545143654
- Jika membuat fitur login dengan WA, itu nanti akan dikirimkan OTP berupa 6 angka (input type tel). Satu akun bisa login multi perangkat. Tokennya nanti akan disimpan di localStorage. Jika nomor WA tidak ada di database, berarti register masuknya itu ya, dan jangan lupa catat waktu registernya

PUTER

- Di bawah ini kesemuanya menggunakan fitur Puter
- Untuk fitur selengkapnya bisa didapatkan di ./knowledge/puter.txt

CONTOH

<!-- MyComponent.svelte -->
<script>
import puter from "@heyputer/puter.js";

function handleClick() {
    puter.ai.chat("hello");
}
</script>

<button on:click={handleClick}>Chat</button>

AI

puter.ai.chat("Explain AI like I'm five!");

DATABASE

// Set a key-value pair
await puter.kv.set('username', 'alice');

// Get a value
const name = await puter.kv.get('username');

// Increment a counter
await puter.kv.incr('pageViews');

// List all keys
const keys = await puter.kv.list();

STORAGE

// Write a file
puter.fs.write('hello.txt', 'Hello, world!');

// Read a file
const content = await puter.fs.read('hello.txt');

// Create a directory
await puter.fs.mkdir('my-folder');

// List files in a directory
const files = await puter.fs.readdir('my-folder');

IMAGE GENERATION

// Generate an image with the default model
const img = await puter.ai.txt2img("A sunset over mountains");
document.body.appendChild(img);

// Use GPT-Image
const gpt = await puter.ai.txt2img("A futuristic city", {
    model: "gpt-image-1.5",
});

// Use Nano Banana
const banana = await puter.ai.txt2img("A peaceful garden", {
    model: "gemini-3-pro-image"
});

VIDEO GENERATION

// Generate a video with test mode (no credits used)
const video = await puter.ai.txt2vid(
    "A sunrise drone shot flying over a calm ocean",
    true // test mode
);
document.body.appendChild(video);

// Generate a clip with Sora
const sora = await puter.ai.txt2vid(
    "A fox sprinting through a snow-covered forest at dusk", {
        model: "sora-2",
    }
);

// Use Google Veo
const veo = await puter.ai.txt2vid("A peaceful garden", {
    model: "veo-3.0-fast"
});

OCR

// Basic text extraction from an image URL
const text = await puter.ai.img2txt(
    "https://assets.puter.site/letter.png"
);
console.log(text);

// Extract text from an uploaded file
const fileInput = document.querySelector('input[type="file"]');
const file = fileInput.files[0];
const result = await puter.ai.img2txt(file);

// Use Mistral OCR provider
const extracted = await puter.ai.img2txt(imageUrl, {
    provider: "mistral"
});

// Process specific pages of a PDF
const pdfText = await puter.ai.img2txt(pdfFile, {
    provider: "aws-textract",
    pages: [1, 2, 3]
});

// Test mode for development
const sample = await puter.ai.img2txt(imageUrl, {
    testMode: true
});

TEXT TO SPEECH

// Basic text to speech with default settings
const audio = await puter.ai.txt2speech("Hello, world!");
audio.play();

// Use neural engine for higher quality
const neural = await puter.ai.txt2speech("Welcome to Puter!", {
    voice: "Joanna",
    engine: "neural"
});

// Use OpenAI TTS
const openai = await puter.ai.txt2speech("This is OpenAI TTS.", {
    provider: "openai",
    model: "tts-1-hd",
    voice: "nova"
});

// Use ElevenLabs for premium voices
const elevenlabs = await puter.ai.txt2speech("Premium voice quality.", {
    provider: "elevenlabs",
    model: "eleven_multilingual_v2"
});

SPEECH TO TEXT

// Basic speech to text transcription
const text = await puter.ai.speech2txt(audioFile);
console.log(text);

// Transcribe from a URL
const result = await puter.ai.speech2txt(
    "https://example.com/audio.mp3"
);

// Use GPT-4o for higher accuracy
const transcript = await puter.ai.speech2txt(audioFile, {
    model: "gpt-4o-transcribe"
});

// Speaker diarization - identify who said what
const diarized = await puter.ai.speech2txt(audioFile, {
    model: "gpt-4o-transcribe-diarize",
    response_format: "diarized_json"
});

// Generate SRT subtitles
const subtitles = await puter.ai.speech2txt(audioFile, {
    response_format: "srt"
});

VOICE CHANGER

// Convert voice from a file path
const audio = await puter.ai.speech2speech("~/recordings/voice.wav");
audio.play();

// Convert voice with a specific voice ID
const converted = await puter.ai.speech2speech(audioFile, {
    voice: '21m00Tcm4TlvDq8ikWAM', // Rachel sample voice
});

// Convert from a Blob or File object
const blob = await recorder.stop();
const result = await puter.ai.speech2speech(blob, {
    remove_background_noise: true,
});

NETWORKING

// Open a TCP socket connection
const socket = new puter.net.Socket("example.com", 80);

// Open a secure TLS socket connection
const tlsSocket = new puter.net.tls.TLSSocket("example.com", 443);

// Send data when connected
socket.on("open", () => {
    socket.write("GET / HTTP/1.1\r\nHost: example.com\r\n\r\n");
});

// Fetch without CORS restrictions
const response = await puter.net.fetch("https://api.example.com");
