function calculateCabin() {
    // UI Elements
    const resultsContainer = document.getElementById('results_container');
    const errorContainer = document.getElementById('error_container');
    const emptyState = document.getElementById('empty_state');
    
    // Hide previous states
    errorContainer.classList.add('hidden');
    resultsContainer.classList.add('hidden');
    emptyState.classList.add('hidden');

    // 1. Get Inputs
    const shaftWidth = parseFloat(document.getElementById('shaft_width').value);
    const shaftDepth = parseFloat(document.getElementById('shaft_depth').value);
    const counterType = parseInt(document.getElementById('counter_type').value);
    const doorType = parseInt(document.getElementById('door_type').value);

    if (isNaN(shaftWidth) || isNaN(shaftDepth)) {
        showError("Please enter valid numerical values for Shaft Width and Depth.");
        return;
    }

    let tol_left, tol_right, tol_back, tol_front;

    // 2. Tolerance Logic (Matched exactly to provided JS)
    if (counterType === 2) {
        if (doorType === 1) {
            tol_left = 185 + 30;
            tol_right = 365 + 30;
            tol_back = 80 + 30;
            tol_front = 140 + 60 + 80;
        } else if (doorType === 2) {
            tol_left = 185 + 30;
            tol_right = 365 + 30;
            tol_back = 80 + 30;
            tol_front = 40 + 90 + 30 + 90 + 60;
        } else {
            showError("Invalid door type selection."); return;
        }
    } else if (counterType === 1) {
        if (doorType === 1) {
            tol_left = 180 + 30;
            tol_right = 180 + 30;
            tol_back = 130 + 130 + 30;
            tol_front = 140 + 60 + 80;
        } else if (doorType === 2) {
            tol_left = 180 + 30;
            tol_right = 180 + 30;
            tol_back = 130 + 130 + 30;
            tol_front = 40 + 90 + 30 + 90 + 60;
        } else {
            showError("Invalid door type selection."); return;
        }
    } else {
        showError("Invalid counter type selection."); return;
    }

    // 3. Cabin Dimensions
    let cabin_width = shaftWidth - (tol_left + tol_right);
    let original_cabin_depth = shaftDepth - (tol_back + tol_front);
    let cabin_depth = original_cabin_depth;

    // 4. Doors Calculation
    let doorsAvailable = [];
    let doorTitle = "";
    if (doorType === 1) {
        doorTitle = "Center Opening Doors Available";
        if (shaftWidth >= (900 * 2 + 200)) doorsAvailable.push("900 mm");
        if (shaftWidth >= (800 * 2 + 200)) doorsAvailable.push("800 mm");
        if (shaftWidth >= (700 * 2 + 200)) doorsAvailable.push("700 mm");
        if (shaftWidth >= (650 * 2 + 200)) doorsAvailable.push("650 mm");
        if (shaftWidth >= (600 * 2 + 200)) doorsAvailable.push("600 mm");
    } else if (doorType === 2) {
        doorTitle = "Telescopic Opening Doors Available";
        if (shaftWidth >= (900 * 1.5 + 200)) doorsAvailable.push("900 mm");
        if (shaftWidth >= (800 * 1.5 + 200)) doorsAvailable.push("800 mm");
        if (shaftWidth >= (700 * 1.5 + 200)) doorsAvailable.push("700 mm");
        if (shaftWidth >= (650 * 1.5 + 200)) doorsAvailable.push("650 mm");
        if (shaftWidth >= (600 * 1.5 + 200)) doorsAvailable.push("600 mm");
    }

    // 5. Area & Passenger Calculation
    let cabin_inside_area = cabin_width * cabin_depth;
    let paxStr = "";
    let depthReduction = 0;

    const areaBase = cabin_width * cabin_depth;
    const M = 1000000;

    if (areaBase < 0.17 * M) {
        showError("The provided shaft size is too small."); return;
    } 
    else if (areaBase >= 0.17 * M && areaBase < 0.34 * M) {
        if (areaBase >= 0.19 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 0.19 * M && (cabin_width * cabin_depth) < 0.34 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "1 Person";
    }
    else if (areaBase >= 0.34 * M && areaBase < 0.51 * M) {
        if (areaBase >= 0.38 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 0.38 * M && (cabin_width * cabin_depth) < 0.51 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "2 Persons";
    }
    else if (areaBase >= 0.51 * M && areaBase < 0.68 * M) {
        if (areaBase >= 0.57 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 0.57 * M && (cabin_width * cabin_depth) < 0.68 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "3 Persons";
    }
    else if (areaBase >= 0.68 * M && areaBase < 0.85 * M) {
        if (areaBase >= 0.77 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 0.77 * M && (cabin_width * cabin_depth) < 0.85 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "4 Persons";
    }
    else if (areaBase >= 0.85 * M && areaBase < 1.00 * M) {
        if (areaBase >= 0.95 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 0.95 * M && (cabin_width * cabin_depth) < 1.00 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "5 Persons";
    }
    else if (areaBase >= 1.00 * M && areaBase < 1.16 * M) {
        if (areaBase >= 1.12 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 1.12 * M && (cabin_width * cabin_depth) < 1.16 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "6 Persons";
    }
    else if (areaBase >= 1.16 * M && areaBase < 1.31 * M) {
        if (areaBase >= 1.28 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 1.28 * M && (cabin_width * cabin_depth) < 1.31 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "7 Persons";
    }
    else if (areaBase >= 1.31 * M && areaBase < 1.46 * M) {
        if (areaBase >= 1.45 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 1.45 * M && (cabin_width * cabin_depth) < 1.46 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "8 Persons";
    }
    else if (areaBase >= 1.46 * M && areaBase < 1.61 * M) {
        if (areaBase >= 1.60 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 1.60 * M && (cabin_width * cabin_depth) < 1.61 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "9 Persons";
    }
    else if (areaBase >= 1.61 * M && areaBase < 1.77 * M) {
        if (areaBase >= 1.76 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 1.76 * M && (cabin_width * cabin_depth) < 1.77 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "10 Persons";
    }
    else if (areaBase >= 1.77 * M && areaBase < 1.92 * M) {
        if (areaBase >= 1.76 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 1.76 * M && (cabin_width * cabin_depth) < 1.92 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "11 Persons";
    }
    else if (areaBase >= 1.92 * M && areaBase < 2.06 * M) {
        if (areaBase >= 2.05 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 2.05 * M && (cabin_width * cabin_depth) < 2.06 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "12 Persons";
    }
    else if (areaBase >= 2.06 * M && areaBase < 2.23 * M) {
        if (areaBase >= 2.20 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 2.20 * M && (cabin_width * cabin_depth) < 2.23 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "13 Persons";
    }
    else if (areaBase >= 2.23 * M && areaBase < 2.35 * M) {
        if (areaBase >= 2.34 * M) {
            for (let i = 0; (cabin_width * cabin_depth) >= 2.34 * M && (cabin_width * cabin_depth) < 2.35 * M; cabin_depth -= 10) { depthReduction += 10; }
        }
        paxStr = "14 Persons";
    }
    else if (areaBase >= 2.35 * M && areaBase < 2.47 * M) {
        paxStr = "15 Persons";
    }
    else {
        showError("The provided shaft size is too large for a standard cabin."); return;
    }

    // Populate Results UI
    document.getElementById('res_width').innerText = cabin_width.toFixed(2) + ' mm';
    document.getElementById('res_depth').innerText = cabin_depth.toFixed(2) + ' mm';
    document.getElementById('res_area').innerText = (cabin_inside_area / M).toFixed(2) + ' M²';
    document.getElementById('res_pax').innerText = paxStr;
    
    // Handle Reduction Text
    const redText = document.getElementById('res_reduction');
    const redAreaText = document.getElementById('res_reduced_area');
    if (depthReduction > 0) {
        redText.innerText = `Cabin depth reduced by ${depthReduction.toFixed(2)} mm from back side to meet capacity rules.`;
        redText.classList.remove('hidden');
        redAreaText.querySelector('span').innerText = ((cabin_width * cabin_depth) / M).toFixed(2) + ' M²';
        redAreaText.classList.remove('hidden');
    } else {
        redText.classList.add('hidden');
        redAreaText.classList.add('hidden');
    }

    // Populate Doors UI
    document.getElementById('door_title').innerText = doorTitle;
    const doorsUl = document.getElementById('res_doors');
    doorsUl.innerHTML = '';
    if (doorsAvailable.length > 0) {
        doorsAvailable.forEach(door => {
            const li = document.createElement('li');
            li.innerText = door;
            doorsUl.appendChild(li);
        });
    } else {
        doorsUl.innerHTML = '<li style="background:#fef2f2; color:#b91c1c;">Shaft width too small for standard doors.</li>';
    }

    // Show results
    resultsContainer.classList.remove('hidden');
}

function showError(msg) {
    const err = document.getElementById('error_container');
    err.innerText = msg;
    err.classList.remove('hidden');
    document.getElementById('empty_state').classList.add('hidden');
    document.getElementById('results_container').classList.add('hidden');
}
