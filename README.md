# Week25
1.Нет, потому что props представляет неизменяемый объект, который предназначен только для чтения.

2.shouldComponentUpdate() 

3.Если в initialObject будут добавляться пары ключ:значение, то в firstObject они не отобразятся т.к. он запишет только начальные значения. В secondObject будут отображатся все пары ключ:значение, неважно будут они добавляться или удалятся дальше.

4.componentDidMount()

5.componentDidCatch

6.Конструктор - специальная функция, которая будет вызываться всякий раз, когда создаётся новый объект. 
важно вызывать функцию super в случаях, когда наш класс расширяет поведение другого класса, который имеет конструктор. Если это не сделать, this.props не будет определён.
Конструкторы используют:
-для создания любых свойств (переменные, начинающиеся с this.) или инициализации состояния компонента на основе полученных props.
-место где вы можете изменять/устанавливать состояние (state), напрямую перезаписывая поле this.state.

7.render() определяет то, что будет выведено на экран, как будет выглядеть компонент. Метод render() в процессе жизни компонента может быть вызван множество раз.

Причины для рендеринга компонента:
Это инициальный рендеринг компонента..
Состояние компонента (или одного из его предков) было обновлено.

8.class Timer extends React.Component {
  constructor{props}
{
  super (props);
  this.state = {
    minutes: 12;
    seconds: 30;
  }
}
render(){
  return (
    <div>
    <img src{icon} alt="timer">
    <p>Timer info: {this.state.minutes}:{this.state.seconds}</p>
    </div>
  );
}
Timer.defaultProps = {
  minutes: 0;
  seconds: 0;
}
}

9.Для нескольких задач можно использовать несколько useEffect для одного и того же компонента. Разделить работу на части и назначьте useEffect для каждой.

10.Можно не передавать второй параметр в хуке useEffect. Если мы не передадим второй аргумент, побочный эффект в функции обратного вызова будет запускаться снова при каждой визуализации компонента.

11.Если useEffect возвращает функцию, React выполнит её только тогда, когда наступит время сбросить эффект.

12.Вызов метода forceUpdate() приведёт к выполнению метода render() в компоненте, пропуская shouldComponentUpdate(). Это вызовет обычные методы жизненного цикла для дочерних компонентов, включая shouldComponentUpdate() каждого дочернего компонента.


Практическое задание.
class Counter extends Component {
  state = {
    count: 0
  };
  handleClick = () => {
    this.setState(({ count }) => ({
      count: count + 1
    }));
  };
  render() {
    return <button onClick={this.handleClick}>{this.state.count}</button>;
  }
}



import React, { useState} from 'react';

const FunctionalComponent = () => {
 const [count, setCount] = React.useState(0);

 return (
   <div>
     <p>count: {count}</p>
     <button onClick={() => setCount(count + 1)}>Click</button>
   </div>
 );
};