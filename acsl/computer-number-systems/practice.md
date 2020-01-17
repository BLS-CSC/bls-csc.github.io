---
title: Computer Number Systems Practice
---

<div id="practice-area">
</div>

<button onclick="grade();">Submit</button>
<button onclick="newProblem();">New problem</button>

<script>
    var practiceArea = document.getElementById("practice-area");
    var fromBase;
    function randNum(base, len) {
        let dig = 1 + Math.floor((base - 1) * Math.random());
        for (let i = 1; i < len; i++) {
            dig *= base;
            dig += Math.floor(base * Math.random());
        }
        return dig;
    }

    function newProblem() {
        fromBase = 2 << Math.floor(Math.random() * 4);
        
        practiceArea.innerHTML = "$$" + randNum(fromBase, 3).toString(fromBase).toUpperCase() + "_{" + fromBase + "} $$";
    }

    newProblem();
</script>