## HTML
```html
<countdown-timer data-expiration-behavior="hide-section" style="--digit-font-size: var(--font-heading-x-small); --text-font-size: var(--font-body-x-small);">
    <div class="countdown__timer">
        <time class="countdown__datetime" datetime="2025-03-31T11:59:00.000-1200">
            <div class="timer">
                <strong class="timer__digit font-heading" data-days="">14</strong>
                <small class="timer__unit">Days</small>
            </div>
            <div class="timer">
                <strong class="timer__digit font-heading" data-hours="">15</strong>
                <small class="timer__unit">Hours</small>
            </div>
            <div class="timer__digit timer">
                <strong class="timer__digit font-heading" data-minutes="">34</strong>
                <small class="timer__unit">Minutes</small>
            </div>
            <div class="timer">
                <strong class="timer__digit font-heading" data-seconds="">51</strong>
                <small class="timer__unit">Seconds</small>
            </div>
        </time>
    </div>
</countdown-timer>
```

## JavaScript
```html
<script>
    function loadResource(type, url) {
        return new Promise((resolve) => {
          if (document.querySelector(`${type === "css" ? "link" : "script"}[href="${url}"], [src="${url}"]`)) {
            return resolve(); // If already loaded, resolve immediately
          }
      
          const element = document.createElement(type === "css" ? "link" : "script");
      
          if (type === "css") {
            element.rel = "stylesheet";
            element.href = url;
          } else {
            element.src = url;
            element.onload = resolve; // Resolve when script is loaded
          }
      
          document.head.appendChild(element);
          if (type === "css") resolve(); // Resolve immediately for CSS
        });
    }

    async function initCountdownTimer() {
        await loadResource("js", "https://cdn.jsdelivr.net/gh/shopifykingbd/skb-countdown-timer/skb-countdown-timer.js");
    }

    // Run the function to load resources
    initCountdownTimer();
</script>
```
