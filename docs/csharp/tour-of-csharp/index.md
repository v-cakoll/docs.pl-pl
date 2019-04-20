---
title: Przewodnik po przykładzie C# - C# przewodnik
description: Jesteś nowym użytkownikiem C#? Poznaj podstawy języka.
ms.date: 04/05/2019
ms.custom: seoapril2019
ms.openlocfilehash: c3a117d660c02702e900b827c2eed9c6b56b5606
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481096"
---
# <a name="a-tour-of-the-c-language"></a>Przewodnik po przykładzie C# języka

C# (Wymowa: "Si Sharp") to prosty, nowoczesny, zorientowany obiektowo i bezpieczny typowo język programowania. Korzenie C# sięgają rodziny języków C i powinien być przyjazny dla programistów C, C++, Java i JavaScript. Ten przewodnik zawiera omówienie głównych składników języka. Jeśli chcesz poznać język za pomocą interaktywnych przykładów, wypróbuj nasze [wprowadzenie do C# ](../tutorials/intro-to-csharp/index.md) samouczki.

C# to język zorientowany obiektowo, ale również obsługuje ***podejście modułowe*** programowania. Współcześnie projektowanie oprogramowania coraz bardziej opiera się na dzielenie całego programu na pakiety w postaci zbiorów niezależnych i samoopisujących się funkcji. Kluczem do takiego podejścia jest wykorzystanie właściwości, metod i zdarzeń tworzonych obiektów; mają one atrybuty, które zapewniają deklaracje informacji o pakiecie; i mogą one być opisane za pomocą oddzielnych dokumentacji. C# udostępnia dokumentację opisującą konstrukcję języka, aby bezpośrednio wyjaśnić pojęcia z nią związane, dzięki czemu język C# jest bardzo naturalny przy tworzeniu i wykorzystywaniu części składowych oprogramowania.

C# ma również bardzo pomocne funkcje służące do tworzenia niezawodnych i trwałych aplikacji: ***Garbage collection*** służący do automatycznego odzyskiwania pamięci zajmowanej przez nieosiągalne i nieużywane obiekty; ***Wychwytywanie wyjątków*** służące do prezechwytywania i obsługiwania błędów; oraz ***Bezpieczne typowanie*** uniemożliwiające odczytywanie niezainicjowane zmiennych, indeksowanie tablic poza ich zakresem, lub wykonywanie rzutowania na siebie nie znanych typów.

C# ma ***własny system typów***. Wszystkie typy danych, w tym typy podstawowe takie jak `int`, czy `double`, dziedziczą z jednego typu głównego `object`. W efekcie wszystkie typy udostępniają zestaw pewnych metod, a wartości dowolnego typu mogą być przechowywane, transportowane i wykorzystywane do różnych operacji w sposób ciągły. Ponadto, C# obsługuje typy odwołań i wartości zdefiniowane przez użytkownika, umożliwiając dynamiczna alokacja obiektów, a także magazynowanie uproszczonych struktur.

Aby upewnić się, że C# programów i bibliotek mogą z czasem ewoluować w sposób zgodny, znacznie większym naciskiem został umieszczony na ***versioning*** w C#projekt. Wiele języków programowania interesuje tego problemu, a w rezultacie, programy napisane w tych języków podziału częściej niż to konieczne, w przypadku nowszych wersjach zależne biblioteki zostały wprowadzone. Aspekty C#przez projekt, który zostały bezpośrednio wpływa uwagi dotyczące wersji zawierają oddzielny `virtual` i `override` modyfikatorów, reguły dla rozwiązania przeciążenia metody i pomoc techniczna dla deklaracji elementu członkowskiego interfejsu jawnego.

## <a name="hello-world"></a>Hello World

Program "Hello, World" tradycyjnie umożliwia wprowadzenie do języka programowania. Poniżej przedstawiono taki program napisany w języku C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Pliki źródłowe C# zazwyczaj mają rozszerzenie `.cs`. Przy założeniu, że program "Hello, World" jest przechowywany w pliku `hello.cs`, program może być skompilowany przy użyciu wiersza poleceń:

```console
csc hello.cs
```

który tworzy pliku wykonywalny o nazwie hello.exe. Dane wyjściowe generowane przez tę aplikację po jej uruchomieniu to:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Polecenie kompiluje dla pełnej struktury i może nie być dostępne na wszystkich platformach.

Program "Hello, World" rozpoczyna się od dyrektywy `using`, która odwołuje się do przestrzeni nazw `System`. Przestrzenie nazw zawierają hierarchiczny sposób organizowania programów C# i biblioteki. Przestrzenie nazw zawierają typy i inne przestrzenie nazw — na przykład przestrzeń nazw `System` zawiera wiele typów, takie jak klasa `Console`, do której odwołuje się program i wiele innych przestrzeni nazw, takich jak `IO` i `Collections`. A dyrektywa `using`, która odwołuje się do danej przestrzeni nazw umożliwia niekwalifikowane korzystanie z typów, które są elementami członkowskimi tej przestrzeni nazw. Z powodu dyrektywy `using`, można użyć polecenia `Console.WriteLine` jako skrót dla `System.Console.WriteLine`.

`Hello` Klasy zadeklarowanej przez program "Hello, World" zawiera jeden element członkowski metodę o nazwie `Main`. `Main` Metody jest zadeklarowana za pomocą modyfikator statyczny. Podczas gdy metody wystąpienia można odwołania konkretnego wystąpienia obiektu otaczającej przy użyciu słowa kluczowego `this`, metody statyczne działać bez odwołania do określonego obiektu. Zgodnie z Konwencją statyczną metodę o nazwie `Main` służy jako punkt wejścia programu.

Dane wyjściowe programu jest generowany przez `WriteLine` metody `Console` klasy w `System` przestrzeni nazw. Ta klasa jest zapewniana przez bibliotek standardowych klas, które domyślnie są automatycznie dołączane do kompilatora.

Istnieje o wiele więcej, aby dowiedzieć się więcej na temat C#.  Poniższe tematy zawierają omówienie elementów C# języka. Te przeglądy będzie podawanie ogólnych informacji o wszystkich elementach języka i zapewnić informacje niezbędne do Dowiedz się więcej na elementy C# języka:

* [Struktura programu](program-structure.md)
  - Dowiedz się, podstawowych pojęć organizacji w C# języka: ***programy***, ***przestrzenie nazw***, ***typy***, ***członków***i ***zestawy***.
* [Typy i zmienne](types-and-variables.md)
  - Dowiedz się więcej o ***typy wartości***, ***typy odwołań***, i ***zmienne*** w C# języka.
* [Wyrażenia](expressions.md)
  - ***Wyrażenia*** są konstruowane na podstawie ***operandów*** i ***operatorów***. Wyrażenia dają wartość.
* [Instrukcje](statements.md)
  - Możesz użyć ***instrukcji*** do działania programu express.
* [Klasy i obiekty](classes-and-objects.md)
  - ***Klasy*** są najbardziej podstawowe języka C# dla typów. ***Obiekty*** są wystąpieniami klasy. Klasy są tworzone przy użyciu ***członków***, które są uwzględniane w tym temacie.
* [Struktury](structs.md)
  - ***Struktury*** są struktur danych, które w przeciwieństwie do klasy, są typami wartości.
* [Tablice](arrays.md)
  - ***Tablicy*** to struktura danych, która zawiera szereg zmiennych, które są dostępne za pośrednictwem obliczanej indeksów.
* [Interfejsy](interfaces.md)
  - ***Interfejsu*** definiuje kontrakt, który może być implementowany przez klas i struktur. Interfejs może zawierać metody, właściwości, zdarzeń i indeksatorów. Interfejs nie zawiera implementacji członków definiuje — jedynie określa elementy członkowskie, które muszą być dostarczane przez klasy lub struktury, które implementują interfejs.
* [Wyliczenia](enums.md)
  - ***Typu wyliczeniowego*** jest typem wartości odrębnych z szeregu nazwanych stałych.
* [Delegaty](delegates.md)
  - A ***typ delegowany*** reprezentuje odwołania do metod z określonego parametru listy i typ zwracany. Delegatów można umożliwić traktować metod jako jednostki, które mogą być przypisane do zmiennych i przekazywane jako parametry. Delegaty są podobne do koncepcji wskaźników funkcji, w przeciwieństwie do innych języków, ale w przeciwieństwie do wskaźników funkcji, obiekty delegowane są zorientowane obiektowo i bezpieczny typowo.
* [Atrybuty](attributes.md)
  * ***Atrybuty*** Włącz programy określić dodatkowe deklaratywne informacje na temat typów, składniki i innych jednostek.

> [!div class="step-by-step"]
> [Next](program-structure.md)
