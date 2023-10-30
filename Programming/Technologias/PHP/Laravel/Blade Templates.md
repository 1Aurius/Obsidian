## Introduction

o blade template permite contstruir paginas dinamicas & layouts. Este oferece uma syntax concisa e expressiva fazendo que seja mais facil de perceber.

## Onde são guardados?

`resources>views`

---

## Apresentar dados

blade permite apresentar dados usando a syntax espacial {{ }}. Dentro desta podemos mostrar dados,variaveis, fazer calculos basicos e usar loops ou condições.

## Directivos

estes diretivos permitem fazer varias operações, incluir partial views(**`@include`**),extender layouts(**`@extends`**),mostrar e esconder conteudos(**`@if`**, **`@unless`**) e mais, estes são marcados por `@`.

## Erança de Templates

Blade permite erança de templates, isto significa que podemos criar um template master e extende-lo para child templates, este podem modificar certos aspetos do master layout com o diretivo **`@section`** e **`@show`** e mais..

## Componentes

blade permite encapsular elementos do UI em diferentes ficheiros e incluilos em um ficheiro blade. Estes permitem reutilização dos componentes e aceitam atributos & dados aumentando assim a legibilidade do código.

## Slots

Slots em ficheiros balde servem para que o master template tenha um espaço para as child blade files possam colocar algo nesse espaço usando **`@slot`** e **`@endslot`**.