<div class="balls">
  <div />
  <div />
  <div />
</div>

<style>
  .balls {
    display: inline-flex;
    flex-flow: row nowrap;
    align-items: center;
    justify-content: space-between;
    margin: 0 auto;
    padding: 1em;
  }
  .balls div {
    width: 0.8em;
    height: 0.8em;
    border-radius: 50%;
    background-color: #ff3e00;
    transform: translateY(-100%);
    animation: wave 0.8s ease-in-out alternate infinite;
  }
  .balls div:nth-of-type(1) {
    animation-delay: -0.4s;
  }
  .balls div:nth-of-type(2) {
    animation-delay: -0.2s;
  }
  @keyframes wave {
    from {
      transform: translateY(-100%);
    }
    to {
      transform: translateY(100%);
    }
  }
</style>
