<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ESL Vocabulary Exercise</title>
    <style>
        :root {
            --teal: #2dd4bf;
            --teal-dark: #14b8a6;
            --green: #86efac;
            --green-dark: #4ade80;
            --gray: #f3f4f6;
            --gray-dark: #e5e7eb;
            --font: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font);
            background-color: #f9fafb;
            color: #1f2937;
            line-height: 1.6;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            padding: 24px;
        }

        h1 {
            color: var(--teal-dark);
            text-align: center;
            margin-bottom: 24px;
        }

        .nav-buttons {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-bottom: 24px;
            flex-wrap: wrap;
        }

        button {
            background: linear-gradient(135deg, var(--teal), var(--teal-dark));
            color: white;
            border: none;
            padding: 10px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s;
        }

        button:hover {
            background: linear-gradient(135deg, var(--teal-dark), #0d9488);
        }

        .section {
            display: none;
        }

        .section.active {
            display: block;
        }

        .vocab-item {
            background: white;
            border: 1px solid var(--gray-dark);
            border-radius: 8px;
            padding: 16px;
            margin-bottom: 16px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
        }

        .vocab-word {
            font-weight: bold;
            color: var(--teal-dark);
            font-size: 1.2em;
            margin-bottom: 4px;
        }

        .vocab-context {
            color: #6b7280;
            font-style: italic;
            margin-bottom: 8px;
        }

        .vocab-meaning {
            margin-bottom: 8px;
        }

        .vocab-example {
            background: var(--gray);
            padding: 12px;
            border-radius: 6px;
            margin-top: 8px;
            font-style: italic;
        }

        .word-bank {
            background: linear-gradient(135deg, var(--green), var(--green-dark));
            color: white;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 16px;
            font-weight: 600;
            text-align: center;
        }

        .fill-gap {
            margin-bottom: 16px;
            padding: 12px;
            background: white;
            border-radius: 6px;
            border: 1px solid var(--gray-dark);
        }

        .fill-gap input {
            padding: 8px;
            border: 1px solid var(--gray-dark);
            border-radius: 4px;
            width: 120px;
            text-align: center;
        }

        .match-container {
            display: flex;
            justify-content: space-between;
            gap: 24px;
        }

        .match-column {
            flex: 1;
        }

        .match-item {
            background: white;
            border: 1px solid var(--gray-dark);
            border-radius: 6px;
            padding: 12px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .match-item:hover {
            background: var(--gray);
        }

        .match-item.selected {
            background: var(--teal);
            color: white;
        }

        .match-item.correct {
            background: var(--green-dark);
            color: white;
        }

        .score {
            position: fixed;
            top: 20px;
            right: 20px;
            background: white;
            padding: 12px 16px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            font-weight: 600;
            color: var(--teal-dark);
        }

        .feedback {
            margin-top: 8px;
            font-size: 0.9em;
            color: #6b7280;
        }

        .correct {
            color: var(--green-dark);
            font-weight: bold;
        }

        .incorrect {
            color: #ef4444;
            font-weight: bold;
        }

        .pronunciation-item {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 16px;
            padding: 12px;
            background: white;
            border-radius: 6px;
            border: 1px solid var(--gray-dark);
        }

        .pronunciation-blank {
            background: var(--gray);
            padding: 8px 12px;
            border-radius: 4px;
            min-width: 120px;
            text-align: center;
            font-weight: 600;
            color: #6b7280;
        }

        .microphone-btn {
            background: var(--teal);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            cursor: pointer;
            font-size: 1.1em;
        }

        .microphone-btn:disabled {
            background: var(--gray-dark);
            cursor: not-allowed;
        }

        @media (max-width: 768px) {
            .match-container {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="score">Score: 0 / 24</div>
    <div class="container">
        <h1>ESL Vocabulary Exercise</h1>

        <div class="nav-buttons">
            <button onclick="showSection('vocab-list')">Vocabulary List</button>
            <button onclick="showSection('fill-gaps-writing')">Fill in the Gaps (Writing)</button>
            <button onclick="showSection('match-definitions')">Match Definitions</button>
            <button onclick="showSection('fill-gaps-pronunciation')">Fill in the Gaps (Pronunciation)</button>
        </div>

        <div id="vocab-list" class="section active">
            <h2>Vocabulary List</h2>
            <div class="vocab-item">
                <div class="vocab-word">acquaintance <button onclick="speak('acquaintance')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as conoscenza)</div>
                <div class="vocab-meaning">Someone you know, but who is not a close friend.</div>
                <div class="vocab-example">I met an old acquaintance at the supermarket yesterday.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">at a certain point <button onclick="speak('at a certain point')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as a un certo punto)</div>
                <div class="vocab-meaning">At a particular time or stage in a process.</div>
                <div class="vocab-example">At a certain point, I realized I had made a mistake.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">melting-pot <button onclick="speak('melting-pot')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as crogiolo di culture)</div>
                <div class="vocab-meaning">A place where different cultures, ideas, or styles mix together.</div>
                <div class="vocab-example">New York City is often called a melting-pot of cultures.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">fire <button onclick="speak('fire')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as licenziare)</div>
                <div class="vocab-meaning">To dismiss someone from their job.</div>
                <div class="vocab-example">The company had to fire several employees due to budget cuts.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">noisy <button onclick="speak('noisy')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as rumoroso)</div>
                <div class="vocab-meaning">Making a lot of noise.</div>
                <div class="vocab-example">The children were very noisy during the movie.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">sooner or later <button onclick="speak('sooner or later')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as prima o poi)</div>
                <div class="vocab-meaning">At some time in the future, eventually.</div>
                <div class="vocab-example">Sooner or later, you'll have to face your fears.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">wings <button onclick="speak('wings')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as ali)</div>
                <div class="vocab-meaning">The limbs that birds use to fly.</div>
                <div class="vocab-example">The eagle spread its wings and flew away.</div>
            </div>
            <div class="vocab-item">
                <div class="vocab-word">well-off <button onclick="speak('well-off')" class="microphone-btn">▶️</button></div>
                <div class="vocab-context">(as benestante)</div>
                <div class="vocab-meaning">Having enough money to live comfortably.</div>
                <div class="vocab-example">They come from a well-off family and never worry about money.</div>
            </div>
        </div>

        <div id="fill-gaps-writing" class="section">
            <h2>Fill in the Gaps (Writing)</h2>
            <div class="word-bank">Word Bank: acquaintance, at a certain point, melting-pot, fire, noisy, sooner or later, wings, well-off</div>
            <div class="fill-gap">
                <span>She is just an ___; we only met once at a conference.</span>
                <input type="text" id="gap1" data-answer="acquaintance">
                <div id="feedback1" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>___ in my life, I decided to change my career completely.</span>
                <input type="text" id="gap2" data-answer="At a certain point">
                <div id="feedback2" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>London is a ___ of different cultures and traditions.</span>
                <input type="text" id="gap3" data-answer="melting-pot">
                <div id="feedback3" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>The manager had to ___ two employees for poor performance.</span>
                <input type="text" id="gap4" data-answer="fire">
                <div id="feedback4" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>The construction site next door is extremely ___ in the morning.</span>
                <input type="text" id="gap5" data-answer="noisy">
                <div id="feedback5" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>___ you will understand the importance of hard work.</span>
                <input type="text" id="gap6" data-answer="Sooner or later">
                <div id="feedback6" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>The butterfly's ___ are beautifully colored.</span>
                <input type="text" id="gap7" data-answer="wings">
                <div id="feedback7" class="feedback"></div>
            </div>
            <div class="fill-gap">
                <span>They are ___ and can afford to travel around the world.</span>
                <input type="text" id="gap8" data-answer="well-off">
                <div id="feedback8" class="feedback"></div>
            </div>
            <div style="display: flex; gap: 12px; margin-top: 20px;">
                <button onclick="checkWritingAnswers()">Check Answers</button>
                <button onclick="resetWritingAnswers()">Reset</button>
            </div>
        </div>

        <div id="match-definitions" class="section">
            <h2>Match Definitions</h2>
            <div class="match-container">
                <div class="match-column">
                    <h3>Words</h3>
                    <div class="match-item" onclick="selectWord(this)" data-word="acquaintance">acquaintance</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="at a certain point">at a certain point</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="melting-pot">melting-pot</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="fire">fire</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="noisy">noisy</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="sooner or later">sooner or later</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="wings">wings</div>
                    <div class="match-item" onclick="selectWord(this)" data-word="well-off">well-off</div>
                </div>
                <div class="match-column">
                    <h3>Definitions</h3>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="Having enough money to live comfortably.">Having enough money to live comfortably.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="At some time in the future, eventually.">At some time in the future, eventually.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="The limbs that birds use to fly.">The limbs that birds use to fly.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="To dismiss someone from their job.">To dismiss someone from their job.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="Someone you know, but who is not a close friend.">Someone you know, but who is not a close friend.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="At a particular time or stage in a process.">At a particular time or stage in a process.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="Making a lot of noise.">Making a lot of noise.</div>
                    <div class="match-item" onclick="selectDefinition(this)" data-definition="A place where different cultures, ideas, or styles mix together.">A place where different cultures, ideas, or styles mix together.</div>
                </div>
            </div>
            <div style="margin-top: 20px;">
                <button onclick="resetMatching()">Reset</button>
            </div>
        </div>

        <div id="fill-gaps-pronunciation" class="section">
            <h2>Fill in the Gaps (Pronunciation)</h2>
            <div class="word-bank">Word Bank: acquaintance, at a certain point, melting-pot, fire, noisy, sooner or later, wings, well-off</div>
            <div class="pronunciation-item">
                <span>___ you will regret not studying harder for your exams.</span>
                <div class="pronunciation-blank" id="pronunciation1" data-answer="Sooner or later">___</div>
                <button class="microphone-btn" onclick="startRecognition(1, 'sooner or later')">🎤</button>
                <div id="pronunciation-feedback1" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>He is just a casual ___ from my university days.</span>
                <div class="pronunciation-blank" id="pronunciation2" data-answer="acquaintance">___</div>
                <button class="microphone-btn" onclick="startRecognition(2, 'acquaintance')">🎤</button>
                <div id="pronunciation-feedback2" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>Toronto is known as a ___ because of its diverse population.</span>
                <div class="pronunciation-blank" id="pronunciation3" data-answer="melting-pot">___</div>
                <button class="microphone-btn" onclick="startRecognition(3, 'melting-pot')">🎤</button>
                <div id="pronunciation-feedback3" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>The company decided to ___ several workers last month.</span>
                <div class="pronunciation-blank" id="pronunciation4" data-answer="fire">___</div>
                <button class="microphone-btn" onclick="startRecognition(4, 'fire')">🎤</button>
                <div id="pronunciation-feedback4" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>The party next door was so ___ that I couldn't sleep.</span>
                <div class="pronunciation-blank" id="pronunciation5" data-answer="noisy">___</div>
                <button class="microphone-btn" onclick="startRecognition(5, 'noisy')">🎤</button>
                <div id="pronunciation-feedback5" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>The bird flapped its ___ and flew into the sky.</span>
                <div class="pronunciation-blank" id="pronunciation6" data-answer="wings">___</div>
                <button class="microphone-btn" onclick="startRecognition(6, 'wings')">🎤</button>
                <div id="pronunciation-feedback6" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>___ in the project, we realized we needed more resources.</span>
                <div class="pronunciation-blank" id="pronunciation7" data-answer="At a certain point">___</div>
                <button class="microphone-btn" onclick="startRecognition(7, 'at a certain point')">🎤</button>
                <div id="pronunciation-feedback7" class="feedback"></div>
            </div>
            <div class="pronunciation-item">
                <span>They are ___ and live in a big house by the lake.</span>
                <div class="pronunciation-blank" id="pronunciation8" data-answer="well-off">___</div>
                <button class="microphone-btn" onclick="startRecognition(8, 'well-off')">🎤</button>
                <div id="pronunciation-feedback8" class="feedback"></div>
            </div>
        </div>
    </div>

    <script>
        let score = 0;
        const totalScore = 24;
        let selectedWord = null;
        let selectedDefinition = null;
        let recognition = null;

        function updateScore() {
            document.querySelector('.score').textContent = `Score: ${score} / ${totalScore}`;
        }

        function showSection(sectionId) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionId).classList.add('active');
        }

        function speak(word) {
            const u = new SpeechSynthesisUtterance(word);
            u.lang = "en-US";
            speechSynthesis.speak(u);
        }

        // Writing Fill in the Gaps
        function checkWritingAnswers() {
            let localScore = 0;
            for (let i = 1; i <= 8; i++) {
                const input = document.getElementById(`gap${i}`);
                const answer = input.dataset.answer;
                const feedback = document.getElementById(`feedback${i}`);
                if (input.value.toLowerCase().trim() === answer.toLowerCase()) {
                    input.style.backgroundColor = '#dcfce7';
                    feedback.textContent = 'Correct!';
                    feedback.className = 'feedback correct';
                    localScore++;
                } else {
                    input.style.backgroundColor = '#fee2e2';
                    feedback.textContent = `Incorrect. The correct answer is "${answer}".`;
                    feedback.className = 'feedback incorrect';
                }
            }
            score += localScore;
            updateScore();
        }

        function resetWritingAnswers() {
            for (let i = 1; i <= 8; i++) {
                const input = document.getElementById(`gap${i}`);
                const feedback = document.getElementById(`feedback${i}`);
                input.value = '';
                input.style.backgroundColor = '';
                feedback.textContent = '';
            }
        }

        // Match Definitions
        function selectWord(element) {
            if (element.classList.contains('correct')) return;
            if (selectedWord) selectedWord.classList.remove('selected');
            selectedWord = element;
            element.classList.add('selected');
            checkMatch();
        }

        function selectDefinition(element) {
            if (element.classList.contains('correct')) return;
            if (selectedDefinition) selectedDefinition.classList.remove('selected');
            selectedDefinition = element;
            element.classList.add('selected');
            checkMatch();
        }

        function checkMatch() {
            if (!selectedWord || !selectedDefinition) return;
            const word = selectedWord.dataset.word;
            const definition = selectedDefinition.dataset.definition;
            const correctDefinition = {
                'acquaintance': 'Someone you know, but who is not a close friend.',
                'at a certain point': 'At a particular time or stage in a process.',
                'melting-pot': 'A place where different cultures, ideas, or styles mix together.',
                'fire': 'To dismiss someone from their job.',
                'noisy': 'Making a lot of noise.',
                'sooner or later': 'At some time in the future, eventually.',
                'wings': 'The limbs that birds use to fly.',
                'well-off': 'Having enough money to live comfortably.'
            };
            if (correctDefinition[word] === definition) {
                selectedWord.classList.add('correct');
                selectedDefinition.classList.add('correct');
                score++;
                updateScore();
            }
            selectedWord = null;
            selectedDefinition = null;
        }

        function resetMatching() {
            document.querySelectorAll('.match-item').forEach(item => {
                item.classList.remove('selected', 'correct');
            });
        }

        // Pronunciation Fill in the Gaps
        function startRecognition(id, expectedWord) {
            const feedbackElement = document.getElementById(`pronunciation-feedback${id}`);
            const blankElement = document.getElementById(`pronunciation${id}`);
            const button = event.target;

            if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
                feedbackElement.textContent = 'Speech recognition not supported in your browser.';
                feedbackElement.className = 'feedback incorrect';
                return;
            }

            button.disabled = true;
            feedbackElement.textContent = 'Listening...';

            const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
            recognition.lang = 'en-US';
            recognition.interimResults = false;
            recognition.maxAlternatives = 1;

            recognition.onresult = function(event) {
                const spokenWord = event.results[0][0].transcript.trim().toLowerCase();
                const normalizedExpected = expectedWord.toLowerCase();
                const normalizedSpoken = spokenWord.toLowerCase();

                if (normalizedSpoken === normalizedExpected) {
                    blankElement.textContent = expectedWord;
                    blankElement.style.backgroundColor = '#dcfce7';
                    feedbackElement.textContent = 'Correct!';
                    feedbackElement.className = 'feedback correct';
                    score++;
                    updateScore();
                } else {
                    feedbackElement.textContent = `Incorrect. Try again!`;
                    feedbackElement.className = 'feedback incorrect';
                }
                button.disabled = false;
            };

            recognition.onerror = function(event) {
                feedbackElement.textContent = 'Error occurred in recognition.';
                feedbackElement.className = 'feedback incorrect';
                button.disabled = false;
            };

            recognition.start();
        }
    </script>
</body>
</html>
