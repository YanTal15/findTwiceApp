//Титульник
function createAppTitle(title){
    let appTitle = document.createElement('h2')
    appTitle.innerHTML = title 
    
    return appTitle

}

let container = document.getElementById('find_twice')
// Счетчики для проверки    
let find = -1 
let findBefere = -1
let finder = 0
//Получаем инпуты и кнопку
let btn = document.querySelector('button')
let rowInput = document.getElementById('row')
let colInput = document.getElementById('col')
//логика кнопки
btn.addEventListener('click', function(e) {
// убираем дефолт действие
e.preventDefault();

let row = rowInput.value
let column = colInput.value
//вызов функции
createAppTitle('Найди пары!')
twiceAppItem(row, column)
//убираем все лишнее
rowInput.remove()
colInput.remove()
btn.remove()
})
btn.addEventListener('click', function(e) {
// убираем дефолт дейтствие
e.preventDefault();
//делаем рестарт-кнопку
let newButton = document.createElement('button')
newButton.textContent = 'Рестарт'
container.append(newButton)
//рестарт
newButton.addEventListener('click', function(e) {
    window.location.reload()
})
let timer = document.createElement('div')
outOfTime = 60
timer.textContent = `Осталось времени: ${outOfTime}`
container.append(timer)

let timeOfGame = setInterval(gameOver, 1000)
function gameOver (){
    if(outOfTime == 0){
        clearInterval(timeOfGame)
        window.location.reload()
    }else{
        
        outOfTime--
        timer.textContent = `Осталось времени: ${outOfTime}`
}}
})

//логика самой игры
const twiceAppItem = (row = 4, column = 4) => {
//проверка четности числа
if(!((row*column)%2 == 0)|| row == 0 || column == 0){
    row = 4;
    column = 4;
}
//генератор случайных чисел
let arrNumber = []
for (i = 1; i < column*row/2 + 1; i++){
    arrNumber.push(i);
    arrNumber.push(i);
}
arrNumber.sort(()=>Math.random()-0.5)
let addNumber = 0
let checkApp = 0
let check = []
for(i = 0; i < row; i++){
    let divRow = document.createElement('div')
    divRow.classList.add('row', 'justify-content-between')  
    container.append(divRow)
    for(x = 0; x < column; x++){
        let divColumn = document.createElement('div')
        let divNumber = document.createElement('div')
        divNumber.classList.add('d-none')
        divNumber.textContent = divColumn.dataset.number
        divColumn.classList.add('col', 'align-items-stretch', 'bg-success', 'm-1', 'column', 'closeCard')  
        divColumn.style.backgroundImage  = 'url(..\img\pngwing.png)'
        divColumn.setAttribute('data-number', arrNumber[addNumber])
        check[addNumber] = 0
        let checker = check[addNumber]

        addNumber++
        let divHeight = container.offsetWidth/column
        //высота
        divColumn.style.height = `${divHeight}px`
        divColumn.style.width = `${divHeight/2}px`
        divColumn.style.fontSize = `${divHeight/2}px`
        divRow.appendChild(divColumn)
        divColumn.appendChild(divNumber)
        divColumn.setAttribute('data-check', true)
        divNumber.textContent = divColumn.dataset.number
        
        //ищем пары

        divColumn.addEventListener('click', function(){
            if(checkApp == divColumn){

                find = -1
                findBefere = -1;

            }
            checkApp = divColumn
            divColumn.dataset.check = false
            divColumn.textContent = divColumn.dataset.number
            if(find == divColumn.textContent){
                divNumber.classList.remove('d-none')
                divColumn.classList.add('bg-danger');
                findBefere.classList.add('bg-danger');
                find = -1;
                findBefere = -1;
                finder = 0;
            }else{
                finder++
                if(finder > 1){
                    find = -1;
                    setTimeout(closeCard, 1000)
                    
                    function closeCard(){
                        divColumn.textContent = ''
                        findBefere.textContent = ''
                        finder = 0
                    }
                }else{
                    find = divColumn.textContent;
                    findBefere = divColumn;
                }
            }
           
            
        })

    }
    
}
}



