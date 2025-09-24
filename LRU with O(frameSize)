//ekhane data initialize korechi
var lastPositions = new Map();
const frameSize = 3;
var frames = new Array(frameSize).fill(null); //shob gulo frame null diye fill korlam
var framesFilled = 0; //frames gulo koyta fill hoyeche ta track korar jonno
console.log("No of frames in LRU: " + frameSize);
var pages = [7, 0, "a", 2, 0, "b", 0, 4, 2, "c", 0, 3, 2, 1, "d", 1, 7, 0, "e"]; // egulo pages jegulo ke search kora hobe kichukkhn por

// ei function diye memory er state gulo print kora hobe
function printMemoryState(page, hit) {
  console.log(frames.join(" ") + "\t" + page + "\t" + (hit ? "H" : "M"));
}

//eta diye least recently used frame tar index ber korbo
function leastRecentlyUsed() {
  let lruIndex = 0;
  for (let i = 1; i < frameSize; i++) {
    if (lastPositions.get(frames[i]) < lastPositions.get(frames[lruIndex])) {
      lruIndex = i;
    }
  }
  return lruIndex;
}

//frames gulo jodi full na hoy tahole page process korar jonno ei function use korbo
function fill(i) {
  for (let j = 0; j < frameSize; j++) {
    const page = pages[i];
    if (frames[j] === page) {
      //HIT
      lastPositions.set(page, i);
      printMemoryState(page, true);
      return;
    } else if (frames[j] === null) {
      //empty frame mane MISS
      frames[j] = page;
      lastPositions.set(page, i);
      framesFilled++;
      printMemoryState(page, false);
      return;
    }
  }
}

function main() {
  console.log("memory State: ");
  const length = pages.length;
  for (let i = 0; i < length; i++) {
    const page = pages[i];
    if (framesFilled < frameSize) {
      fill(i); //frames gulo jodi full na hoy tahole fill function call korbo
    } else {
      if (frames.includes(page)) {
        //HIT
        lastPositions.set(page, i);
        printMemoryState(page, true);
        continue;
      }
      //MISS hole ekhane asbe
      let lruIndex = leastRecentlyUsed();
      frames[lruIndex] = page;
      lastPositions.set(page, i);
      printMemoryState(page, false);
    }
  }
}
main();
