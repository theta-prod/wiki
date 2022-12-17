# [Tutorial] No sleep browser

- **Metadata** : `type: Tutorial` `scope: script` 
- **Techs Need** : `colab` `Javascript`
- **Status** : `need-review`

<br/><br/>
## ✨ You should already know

> Nothing

👩‍💻 👨‍💻

<br/><br/>
## ✨ About the wiki

- `Situation:`  當我們在使用colab執行長時間任務（訓練），免費帳戶可連續執行12h，但是由於瀏覽器睡眠（90min）導致訓練中斷 
- `Target:`  固定時間喚醒瀏覽器
- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| Script |  可以在瀏覽器的console上執行js來喚醒 | - |


<br/><br/>
## ✨  Sections

<br/>

---
### **Script**
> 可以在瀏覽器的console上執行js來喚醒，以colab為例。

```
function ClickConnect() {
  console.log('Working')
  document
    .querySelector('#top-toolbar > colab-connect-button')
    .shadowRoot.querySelector('#connect')
    .click()
}
setInterval(ClickConnect, 60000)
```

<br/><br/>


---
