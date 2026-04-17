async function generateCaptions(){
    const text = document.getElementById("inputText").value;
    const output = document.getElementById("output");

    if(!text){
        output.innerHTML = "⚠️ Enter text first";
        return;
    }

    output.innerHTML = "⏳ Generating AI captions...";

    await new Promise(r => setTimeout(r, 1200)); // AI feel delay

    let styles = [
        `✨ ${text} — a moment worth remembering.`,
        `🔥 When ${text}, everything changes.`,
        `💔 ${text} hits different at night.`,
        `😎 ${text} is not just a vibe, it's a lifestyle.`,
        `🌸 ${text} feels like a dream.`,
        `🚀 ${text} going next level.`,
        `💭 Can't stop thinking about ${text}`,
        `🎬 ${text} story begins here.`,
        `❤️ ${text} forever and always.`,
        `⚡ ${text} energy unmatched.`,
        `🌍 ${text} in my world.`,
        `💥 ${text} impact is real.`,
        `🎵 ${text} rhythm of life.`,
        `📸 ${text} captured perfectly.`,
        `👑 ${text} king vibes only.`
    ];

    let result = [];

    for(let i=0;i<12;i++){
        const cap = styles[Math.floor(Math.random()*styles.length)];
        result.push(`
        <div class="caption">
            <span>${cap}</span>
            <button class="copyBtn" onclick="copyText('${cap}')">Copy</button>
        </div>
        `);
    }

    output.innerHTML = result.join("");
}
