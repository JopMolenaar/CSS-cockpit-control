## Proces CSS tot the rescue 

### Week 1

```css
main > div:nth-child(2) > div {
    height:45vh;
    width: 250%;
    transform-style: preserve-3d;
    --dot-bg: black;
    --dot-color: white;
    --dot-size: 1px;
    --dot-space: 22px;
    background:
          linear-gradient(90deg, var(--dot-bg) calc(var(--dot-space) - var(--dot-size)), transparent 1%) center / var(--dot-space) var(--dot-space),
          linear-gradient(var(--dot-bg) calc(var(--dot-space) - var(--dot-size)), transparent 1%) center / var(--dot-space) var(--dot-space),
          var(--dot-color);
}

main > div:nth-child(2) > div:nth-child(1) {
    transform: rotateX(-24deg) translateY(14%) translateX(-25%);
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    flex-wrap: wrap;
    animation: starsMoving1 2s linear infinite;
}
@keyframes starsMoving1 {
    0% {
        transform: rotateX(-24deg) translateY(28.8%) translateX(-25%);
    }
    100% {
        transform: rotateX(-24deg) translateY(14%) translateX(-25%);
    }
}
main > div:nth-child(2) > div:nth-child(2) {
    transform: rotateX(32deg) translateY(1%) translateX(-25%);
    animation: starsMoving2 2s linear infinite;
}
@keyframes starsMoving2 {
    0% {
        transform: rotateX(32deg) translateY(-13.65%) translateX(-25%);
    }
    100% {
        transform: rotateX(32deg) translateY(1%) translateX(-25%);
    }
}
```

### Week 2



