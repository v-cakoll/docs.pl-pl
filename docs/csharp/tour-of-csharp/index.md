---
title: Przewodnik po przykładzie C# - C# przewodnik
description: Jesteś nowym użytkownikiem C#? Poznaj podstawy języka.
ms.date: 04/05/2019
ms.custom: seoapril2019
ms.openlocfilehash: d1373b65d6cb821871c68574662360c1431d79cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152064"
---
# <a name="a-tour-of-the-c-language"></a>Przewodnik po przykładzie C# języka

C# (Wymowa: "Zobacz Sharp") to proste, nowoczesnych, zorientowane obiektowo i bezpieczny typowo język programowania. C#korzenie jego rodziny C języków, będzie znane w programowaniu w języku C, C++, Java i JavaScript. Ten przewodnik zawiera omówienie głównych składników języka. Jeśli chcesz poznać język za pomocą interaktywnych przykłady, Wypróbuj nasz [wprowadzenie do C# ](../tutorials/intro-to-csharp/index.md) samouczków.

C# to język obiektowy, ale C# dalsze obejmuje obsługę ***zorientowanego na*** programowania. Projektowania oprogramowania współczesnych coraz bardziej opiera się na składniki oprogramowania w postaci pakietów niezależna i samoopisujące funkcji. Kluczem do takich składników jest, czy stanowią one model programowania za pomocą właściwości, metod i zdarzeń; mają atrybuty, które zapewniają deklaracyjne informacje o składniku; i obejmują one we własnej dokumentacji. C#udostępnia konstrukcji języka, aby bezpośrednio obsługują te pojęcia, dzięki czemu C# bardzo języka naturalnego, w której do tworzenia i używania składników oprogramowania.

Kilka C# funkcje pomocy do tworzenia niezawodnych i trwałych aplikacji: ***Wyrzucanie elementów bezużytecznych*** automatycznie odzyskuje pamięć zajmowanych przez nieosiągalne obiekty nieużywane; ***wyjątków*** ze strukturą i rozszerzalny podejście do wykrywania błędów i odzyskiwania; i ***bezpieczny*** projekt języka umożliwia odczytywanie niezainicjowane zmienne Indeksowanie tablic poza ich zakresem, lub wykonać unchecked typu rzutowania.

C# ma ***unified system typów***. Wszystkie C# typów, w tym typów podstawowych takich jak `int` i `double`, dziedziczą z jednym elementem głównym `object` typu. W efekcie wszystkie typy udostępnić zestaw typowych operacji, a wartości dowolnego typu mogą być przechowywane, transportowane i wykonywane są operacje w sposób ciągły. Ponadto, C# obsługuje typy odwołań zdefiniowanych przez użytkownika i typów wartości, umożliwiając dynamiczna alokacja obiektów, a także magazynu w tekście uproszczone struktur.

Aby upewnić się, że C# programów i bibliotek mogą z czasem ewoluować w sposób zgodny, znacznie większym naciskiem został umieszczony na ***versioning*** w C#projekt. Wiele języków programowania interesuje tego problemu, a w rezultacie, programy napisane w tych języków podziału częściej niż to konieczne, w przypadku nowszych wersjach zależne biblioteki zostały wprowadzone. Aspekty C#przez projekt, który zostały bezpośrednio wpływa uwagi dotyczące wersji zawierają oddzielny `virtual` i `override` modyfikatorów, reguły dla rozwiązania przeciążenia metody i pomoc techniczna dla deklaracji elementu członkowskiego interfejsu jawnego.

## <a name="hello-world"></a>Cześć ludzie

Program "Hello, World" tradycyjnie umożliwia wprowadzenie języka programowania. Poniżej przedstawiono w języku C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Pliki źródłowe C# zazwyczaj mają rozszerzenie pliku `.cs`. Przy założeniu, że program "Hello, World" jest przechowywany w pliku `hello.cs`, program może być skompilowana przy użyciu wiersza polecenia:

```console
csc hello.cs
```

który tworzy zestaw pliku wykonywalnego o nazwie hello.exe. Dane wyjściowe generowane przez tę aplikację po jej uruchomieniu są:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Polecenie kompiluje dla pełnej struktury i mogą nie być dostępne na wszystkich platformach.

Program "Hello, World" rozpoczyna się od `using` dyrektywę, który odwołuje się do `System` przestrzeni nazw. Przestrzenie nazw zawierają hierarchiczny sposób organizowania programów C# i biblioteki. Przestrzenie nazw zawierają typy i inne przestrzenie nazw — na przykład `System` przestrzeń nazw zawiera wiele typów, takie jak `Console` klasy, do którego odwołuje się program i wiele innych przestrzeniach nazw, takich jak `IO` i `Collections`. A `using` dyrektywę, który odwołuje się do danej przestrzeni nazw umożliwia niekwalifikowanej korzystanie z typów, które są elementami członkowskimi tej przestrzeni nazw. Z powodu `using` dyrektywy, można użyć programu `Console.WriteLine` jako skrót dla `System.Console.WriteLine`.

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
