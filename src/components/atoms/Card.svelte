<style lang="scss">
@import "../../styles/common.scss";
.card{
  border: 1px solid $v-attentionColor;

  &_title{
    text-align: center;
    margin: 5px 0;
    font-weight: bold;
  }

  &_text{
    text-align: center;
    margin-bottom: 10px;
  }
}

p{
  text-align: center;
}
</style>

<li class="card">
  <h2 class="card_title">カードタイトル</h2>
  <p class="card_text">テキストテキストテキスト</p>
  <p>親コンポーネント</p>
</li>