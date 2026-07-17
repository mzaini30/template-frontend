FITUR PREMIUM

- Ketika ada fitur-fitur yang bagus di website, jadikan dia fitur premium
- Fitur premium ini bisa diakses hanya jika ada data ini di localStorage.lisensi : iahsdaslkuyioamdfklayiwojaklshjdfljahiowfjalkshjdilaiofnalksdjklgfaslkdjfalksr8oiawjlkfalksdjalkhskofajskldfjalksjdflkajsdlkfjaiowfjnmlkasjdflkajslkdfjalksjfklajlkfjaslkf
- Jika tidak ada teks tersebut di localStorage.lisensi, maka kasih tau user bahwa bisa mendapatkan lisensinya di https://lynk.id/zenhacker/123 (harga 30 ribu rupiah), terus, ada form untuk memasukkan teks lisensinya yang nantinya akan disimpan di localStorage.lisensi

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

WHATSAPP

- Untuk komunikasi dengan WhatsApp menggunakan Sidobe yang docsnya berada di knowledge/sidobe.txt
- API keynya adalah bZYMoXDsIyjUVgognpKrdYylgwKzAOCHgHFjbdLeOJwosdtjAv
- Untuk nomor WhatsApp berformat 081234567890 akan secara otomatis diubah menjadi format +6281545143654

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

AI GATEWAY

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

AUTH

// Sign in when the user clicks your button
document.getElementById("sign-in").addEventListener("click", async () => {
    await puter.auth.signIn();

    // Now you know who they are
    const user = await puter.auth.getUser();
    puter.print(`Welcome, ${user.username}!`);

    // Saved to their account, scoped to your app
    await puter.kv.set("visits", 1);
});

// Check auth status any time, no await needed
if (puter.auth.isSignedIn()) {
    puter.print("This user is already signed in.");
}

// End the session
// puter.auth.signOut();

PEER

// Host: start a peer server and share the invite code
const server = await puter.peer.serve();
console.log(`Invite code: ${server.inviteCode}`);

server.addEventListener("connection", (event) => {
    const conn = event.conn;
    conn.addEventListener("open", () => conn.send("Hello from the host!"));
    conn.addEventListener("message", (msg) => console.log("Peer says:", msg.data));
});

// Client: connect using the invite code
const conn = await puter.peer.connect(inviteCode);
conn.addEventListener("open", () => conn.send("Hello from the client!"));
conn.addEventListener("message", (msg) => console.log("Host says:", msg.data));

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