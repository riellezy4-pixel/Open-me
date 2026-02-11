<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Moment for Us</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=EB+Garamond:ital@0;1&display=swap" rel="stylesheet">
    <style>
        :root {
            --burgundy: #630d16;
            --cream: #f9f4e8;
            --text-dark: #3d0a0f;
        }

        body, html {
            margin: 0; padding: 0;
            background-color: #000;
            font-family: 'EB Garamond', serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: var(--text-dark);
            overflow-x: hidden;
        }

        /* LACE CARD STYLE */
        .lace-card {
            display: none;
            width: 90%;
            max-width: 500px;
            background: var(--cream);
            padding: 40px 20px;
            border: 12px solid var(--burgundy);
            outline: 4px solid var(--cream);
            position: relative;
            text-align: center;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8);
        }

        h1, h2, h3 { font-family: 'Playfair Display', serif; color: var(--burgundy); }

        /* ENVELOPE (9574.jpg) */
        #stage-1 {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
        }
        .env-bg {
            width: 320px; height: 220px;
            background: var(--burgundy);
            position: relative;
            display: flex; justify-content: center; align-items: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        .env-seal { font-size: 55px; filter: drop-shadow(0 4px 4px rgba(0,0,0,0.5)); }

        /* BUTTONS & CAT (9575-9577.jpg) */
        .btn-group button {
            padding: 10px 25px; margin: 10px;
            background: var(--burgundy); color: white;
            border: none; cursor: pointer; font-family: 'Playfair Display', serif;
            font-size: 1.1rem;
        }
        #no-btn { background: #eee; color: var(--burgundy); border: 1px solid var(--burgundy); transition: 0.1s; }
        .crying-cat { display: none; margin-top: 15px; }
        .crying-cat img { width: 120px; }

        /* HEART CHOICE (9580.jpg) */
        .heart-grid { display: flex; justify-content: space-around; margin-top: 25px; }
        .heart-choice { font-size: 50px; cursor: pointer; transition: 0.3s; filter: hue-rotate(320deg); }
        .heart-choice:hover { transform: scale(1.2); }

        /* LETTER SCROLL */
        .letter-scroll {
            max-height: 55vh; overflow-y: auto; text-align: justify;
            padding: 20px; border-top: 1px solid var(--burgundy); line-height: 1.8;
            font-size: 1.1rem;
        }
        .letter-scroll p { margin-bottom: 20px; }

        /* CUSTOM SCROLLBAR */
        .letter-scroll::-webkit-scrollbar { width: 5px; }
        .letter-scroll::-webkit-scrollbar-track { background: var(--cream); }
        .letter-scroll::-webkit-scrollbar-thumb { background: var(--burgundy); }
    </style>
</head>
<body>

    <div id="stage-1" onclick="showStage(2)">
        <div class="env-bg">
            <div class="env-seal">🤎</div>
        </div>
        <p style="color: white; margin-top: 20px; letter-spacing: 3px; font-size: 0.9rem;">OPEN THE ENVELOPE</p>
    </div>

    <div id="stage-2" class="lace-card">
        <h1>Will You Be My Valentine?</h1>
        <div class="btn-group">
            <button onclick="showStage(4)">YES</button>
            <button id="no-btn" onmouseover="moveNo()">NO</button>
        </div>
        <div id="cat-guilt" class="crying-cat">
            <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJndXp4ZzR6bmN6ZzR6bmN6ZzR6bmN6ZzR6bmN6ZzR6bmN6ZzR6JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1z/OPU6wUKARAtaU/giphy.gif">
            <p>Oh, why not, my love?</p>
        </div>
    </div>

    <div id="stage-4" class="lace-card">
        <h1>You just made my heart so happy!</h1>
        <p style="font-size: 3rem;">❤️</p>
        <button onclick="showStage(5)">Next</button>
    </div>

    <div id="stage-5" class="lace-card">
        <h1>Before we go on, take a moment...</h1>
        <button onclick="showStage(6)">Click here</button>
    </div>

    <div id="stage-6" class="lace-card">
        <h3>3 Reasons Why I Love You</h3>
        <div style="text-align: left; margin: 20px 0;">
            <p>1. <b>You are my safe harbor:</b> Being with you feels like finally coming home.</p>
            <p>2. <b>You make me better:</b> You inspire me to be my best self every day.</p>
            <p>3. <b>You’re my best friend:</b> You are the first person I want to talk to, always.</p>
        </div>
        <hr style="border-color: var(--burgundy);">
        <h3 style="font-style: italic; font-size: 1.1rem;">Every moment with you is my favorite memory.</h3>
        <p>Choose one heart to continue</p>
        <div class="heart-grid">
            <span class="heart-choice" onclick="showStage(7)">❤️</span>
            <span class="heart-choice" onclick="showStage(7)">❤️</span>
            <span class="heart-choice" onclick="showStage(7)">❤️</span>
        </div>
    </div>

    <div id="stage-7" class="lace-card">
        <h3>3 Things I Love About You</h3>
        <div style="text-align: left; margin: 20px 0;">
            <p>1. <b>Your Perspective:</b> I love how you see beauty in the small details.</p>
            <p>2. <b>Your Warmth:</b> Your presence alone can make a bad day disappear.</p>
            <p>3. <b>Your Passion:</b> I love the way your eyes light up when you're excited.</p>
        </div>
        <hr style="border-color: var(--burgundy);">
        <p>Pick another heart for a final surprise...</p>
        <div class="heart-grid">
            <span class="heart-choice" onclick="showStage(8)">❤️</span>
            <span class="heart-choice" onclick="showStage(8)">❤️</span>
            <span class="heart-choice" onclick="showStage(8)">❤️</span>
        </div>
    </div>

    <div id="stage-8" class="lace-card">
        <iframe width="100%" height="60" src="https://www.youtube.com/embed/S3wytd6ZbXc?autoplay=1" frameborder="0" allow="autoplay"></iframe>
        <h2 style="font-size: 1.5rem; margin-top: 20px;">My love,</h2>
        <div class="letter-scroll">
            <p>I’ve been thinking about you a lot lately, about how you walked into my life in the most unexpected way and somehow made everything feel lighter. There are days when the world feels loud and heavy, and then there’s you—your laugh, your presence, the calm you bring even when things get messy. I don’t always say this out loud, but having you in my life is one of the things I’m most grateful for. You remind me that love doesn’t have to be perfect to be real. It just has to be honest.</p>
            
            <p>Thank you for choosing me every day, even on the days when I’m not at my best. Thank you for being patient when I’m moody, tired, or quiet. Thank you for listening to my stories, even the random ones that don’t always make sense. Thank you for caring about the small details—how I’m feeling, what made me smile, what made my day hard. Those little things might seem simple, but they mean so much to me. They make me feel seen, heard, and understood.</p>

            <p>I love how you make ordinary moments feel special. The simple talks, the jokes we share, the times we just sit and exist together—those moments are my favorite. They remind me that love isn’t only about big gestures. It’s about choosing to show up, choosing to care, choosing to stay kind even when things aren’t easy. With you, I’ve learned that comfort can be beautiful. I’ve learned that peace can feel like home. You inspire me to be better—not in a pressured way, but in a gentle way.</p>

            <p>You make me want to grow, to be more patient, to be more understanding, to be braver with my feelings. When I doubt myself, you remind me of my worth. When I’m scared to try, you encourage me to take the step anyway. You don’t just love me; you believe in me, and that’s something I hold close to my heart.</p>

            <p>I know we’re both still learning. We’re learning how to communicate, how to handle misunderstandings, how to be there for each other when life gets tough. There will be days when we don’t agree, days when we’re tired, days when emotions run high. But I want you to know that I choose to work through those days with you. I choose patience over pride. I choose honesty over silence. I choose us, not because we’re perfect, but because we’re willing to grow together.</p>

            <p>If I ever get quiet, please know it doesn’t mean I love you any less. Sometimes my heart just needs a moment to breathe. And if you ever feel unsure, I hope you remember this: you matter to me. Your feelings matter to me. Your dreams matter to me. I care about the things that make you excited, the things that worry you, and the things you’re still figuring out. I want to be someone who supports you, not someone who holds you back.</p>

            <p>I admire your strength, even when you don’t see it in yourself. I admire how you try, how you keep going, how you show up for the people you care about. You don’t have to be perfect for me to love you. I love you for who you are, for the effort you give, for the heart you carry. And on the days you feel like you’re not enough, I hope you hear my voice in your mind telling you that you are more than enough.</p>

            <p>Being with you makes me hopeful about the future—not in a pressured way, but in a gentle, steady way. I imagine more shared laughs, more late-night talks, more quiet moments where everything feels okay because we’re together. I don’t know exactly what tomorrow will bring, but I know I want to face it with you by my side, learning, growing, and choosing each other again and again.</p>

            <p>Thank you for being my safe place. Thank you for being my comfort. Thank you for being my favorite person to talk to when my day has been long. Thank you for reminding me that love can be kind, patient, and real. I promise to keep trying to be someone who listens, who understands, and who shows love not just with words, but with actions.</p>

            <p>No matter how busy life gets, no matter how loud the world becomes, I hope you always remember this: you are important to me. You are valued. You are cared for deeply. I’m proud of you for who you are and for who you’re becoming. And I’m grateful that out of all the people in this world, I get to walk this part of life with you.</p>

            <p style="text-align: right; font-family: 'Playfair Display', serif; font-style: italic; font-size: 1.3rem;">With all my love,<br>Always yours 🤍</p>
        </div>
    </div>

    <script>
        function showStage(stageNum) {
            for(let i=1; i<=8; i++){
                let s = document.getElementById('stage-'+i);
                if(s) s.style.display = 'none';
            }
            document.getElementById('stage-'+stageNum).style.display = 'block';
        }

        function moveNo() {
            document.getElementById('cat-guilt').style.display = 'block';
            let btn = document.getElementById('no-btn');
            btn.style.position = 'absolute';
            btn.style.left = Math.random() * 80 + '%';
            btn.style.top = Math.random() * 80 + '%';
        }
    </script>
</body>
</html>
