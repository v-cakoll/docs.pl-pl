---
title: W samouczku języka C# — przewodnik C#
description: Jesteś nowym użytkownikiem C#? Poznaj podstawy języka.
ms.date: 08/10/2016
ms.assetid: ebc727cd-8112-42e7-b59c-3c2873ad661c
ms.openlocfilehash: bdb8a84083b391c27d39f5c566a01b2db318123f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="a-tour-of-the-c-language"></a>Samouczek języka C#  

C# (wyraźnym "Zobacz Sharp") jest proste, Nowoczesny zorientowany obiektowo i bezpieczny język programowania. C# ma jego katalogów głównych w rodzinie języków C i będzie znane programistów C, C++, Java i JavaScript.

C# jest zorientowany obiektowo język, ale C# dalsze obejmuje obsługę ***zorientowany*** programowania. Nowoczesne oprogramowanie — projekt zależy coraz składników oprogramowania w formie autonomiczne i samoopisujące pakietów funkcji. Kluczem do takich składników jest promowania model programowania z właściwości, metod i zdarzeń; mają one atrybuty, które zawierają deklaratywne informacje o składniku; i obejmują one własnej dokumentacji. C# zawiera konstrukcji językowych do obsługi bezpośrednio tych pojęć wprowadzania C# bardzo języka naturalnego, w którym do utworzenia i użycia składników oprogramowania.

Kilka funkcji C# pomocy w konstrukcji aplikacji niezawodny i trwałe: ***wyrzucanie elementów bezużytecznych*** automatycznie zwraca pamięci zajmowane przez nieosiągalny nieużywane obiekty; ***obsługi wyjątków*** zapewnia strukturalnych i rozszerzalny podejście do wykrywania błędów i odzyskiwania; i ***bezpieczne*** projektu języka uniemożliwia odczytywać niezainicjowany zmienne tablic indeks poza zakresem ich lub wykonania rzutowania typów niezaznaczone.

C# ma ***unified system typów***. Wszystkie typy C#, tym typy pierwotne, takie jak `int` i `double`, dziedziczą z jednym elementem głównym `object` typu. W związku z tym wszystkie typy mają zestaw typowych operacji, a wartości dowolnego typu mogą być przechowywane, transportowane i wykonywane są operacje w sposób ciągły. Ponadto C# obsługuje zarówno typy odwołań zdefiniowanych przez użytkownika i typów wartości, umożliwiając dynamiczna alokacja obiektów, a także magazynu w wierszu lekkie struktur.

Aby upewnić się, że programów C# i biblioteki można rozwijać wraz z upływem czasu, w sposób zgodny, znacznie nacisk został umieszczony na ***versioning*** w C# w projekcie. Wiele języków programowania interesuje tego problemu i w związku z tym wprowadzono programów napisanych w tych języków podziału częściej niż niezbędne w przypadku nowszych wersji zależnych bibliotek. Aspekty projektu C# w, które zostały bezpośrednio wpływa zagadnienia dotyczące wersji obejmują szczegółowych `virtual` i `override` modyfikatory, reguły Rozpoznanie przeciążenia metody i pomoc techniczna dla deklaracji elementu członkowskiego interfejsu jawnego.

## <a name="hello-world"></a>Cześć ludzie

Wprowadzenie do języka programowania tradycyjnie służy program "Hello, World". Poniżej przedstawiono w języku C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Pliki źródłowe C# zazwyczaj mają rozszerzenie `.cs`. Przy założeniu, że program "Hello, World" jest przechowywany w pliku `hello.cs`, program może być kompilowana przy użyciu wiersza polecenia:

```console
csc hello.cs
```

pozwalającą na uzyskanie pliku wykonywalnego o nazwie hello.exe zestawu. Dane wyjściowe, generowane przez tę aplikację, po jego uruchomieniu jest:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Polecenie kompiluje pełne Framework i nie mogą być dostępne na wszystkich platformach.


Program "Hello, World" rozpoczyna się od `using` dyrektywy, który odwołuje się do `System` przestrzeni nazw. Przestrzenie nazw pozwalają hierarchiczne organizowanie C# programów i bibliotek. Przestrzenie nazw zawierają typy i innych przestrzeniach nazw — na przykład `System` przestrzeń nazw zawiera wiele typów, takie jak `Console` klasy, do których odwołuje się program i wiele innych przestrzeniach nazw, takich jak `IO` i `Collections`. A `using` dyrektywy, który odwołuje się do danej przestrzeni nazw umożliwia niekwalifikowane korzystanie z typów, które są członkami tej przestrzeni nazw. Z powodu `using` dyrektywy, można użyć programu `Console.WriteLine` jako skrócona forma `System.Console.WriteLine`.

`Hello` Klasy zadeklarowanej przez program "Hello, World" zawiera jeden element członkowski, metodę o nazwie `Main`. `Main` Metoda jest zadeklarowana z modyfikator statyczny. Gdy wystąpienie metody może odwoływać się konkretnego wystąpienia obiektu otaczającego za pomocą słowa kluczowego `this`, metody statyczne działać bez odwołania do określonego obiektu. Konwencja, statycznej metody o nazwie `Main` służy jako punkt wejścia programu.

Dane wyjściowe programu jest generowany przez `WriteLine` metody `Console` klasy w `System` przestrzeni nazw. Ta klasa jest zapewniana przez bibliotek klas standardowych, które domyślnie automatycznie przywoływane przez kompilator.

Istnieje wiele Aby dowiedzieć się więcej o języku C#.  Poniższe tematy zawierają omówienie elementy języka C#. Omówienie tych zapewni podstawowe informacje o wszystkich elementach języka i zapewnić informacje niezbędne do bardziej Poznaj elementy języka C#:

* [Struktura programu](program-structure.md)
    - Dowiedz się więcej podstawowych pojęć organizacji w języku C#: ***programy***, ***przestrzeni nazw***, ***typy***, ***członków***, i  ***zestawy***.
* [Typy i zmienne](types-and-variables.md)
    - Dowiedz się więcej o ***typów wartości***, ***typy referencyjne***, i ***zmienne*** w języku C#.
* [Wyrażenia](expressions.md)
    - ***Wyrażenia*** są tworzone na podstawie ***operandy*** i ***operatory***. Wyrażenia tworzy wartości.
* [Instrukcje](statements.md)
    - Możesz użyć ***instrukcje*** Express działania programu.
* [Klasy i obiekty](classes-and-objects.md)
    - ***Klasy*** są najbardziej podstawowe C# dla typów. ***Obiekty*** są wystąpieniami klasy. Klasy są tworzone przy użyciu ***członków***, które są uwzględniane w tym temacie.
* [Struktury](structs.md)
    - ***Struktury*** są struktury danych, które w przeciwieństwie do klasy, są typy wartości.
* [Tablice](arrays.md)
    - ***Tablicy*** jest strukturą danych, która zawiera szereg zmiennych, które są udostępniane przez obliczoną indeksów.
* [Interfejsy](interfaces.md)
    - ***Interfejsu*** definiuje kontrakt może być zaimplementowany przez klasy i struktury. Interfejs może zawierać metod, właściwości, zdarzeń i indeksatorów. Interfejs nie zawiera implementacji elementów członkowskich definiuje — Określa on tylko elementy członkowskie, które muszą zostać dostarczone przez klasy lub struktury, który implementuje interfejs.
* [Wyliczenia](enums.md)
    - ***Typu wyliczeniowego*** jest typem unikatowych wartości przy użyciu zestawu stałe nazwane.
* [Delegaci](delegates.md)
    - A ***typ delegata*** reprezentuje odwołania do metody z określonego parametru listę i typ zwracany. Obiekty delegowane umożliwiają traktować jako jednostek, które można przypisywać do zmiennych i przekazywane jako parametry metody. Obiekty delegowane są podobne do koncepcji znaleziono w przypadku niektórych języków innych wskaźników funkcji, ale w przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowo i bezpieczne.
* [Atrybuty](attributes.md)
    * ***Atrybuty*** Włącz programy określić dodatkowe deklaratywne informacji o typach, członków i inne jednostki.

>[!div class="step-by-step"]
[Next](program-structure.md)
