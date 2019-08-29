---
title: C# C# poradniku
description: Jesteś nowym C#? Poznaj podstawy języka.
ms.date: 04/05/2019
ms.custom: seoapril2019
ms.openlocfilehash: eaaa5a259f0776a2749ed899d0406aee041a8442
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105649"
---
# <a name="a-tour-of-the-c-language"></a>Przewodnik po C# języku

C# (wymowa: „si szarp”) to prosty, nowoczesny, zorientowany obiektowo i bezpieczny język programowania. Wywodzi się z rodziny języków C i od razu wyda się znajomy programistom pracującym w językach C, C++, Java i JavaScript. Ten przewodnik zawiera omówienie głównych składników języka C#. Aby poznać ten język za pomocą przykładów interaktywnych, wypróbuj nasze samouczki [Wprowadzenie do C#](../tutorials/intro-to-csharp/index.md).

C# to język zorientowany obiektowo, ale obsługuje również programowanie ***zorientowane na składniki***. Tworzone dziś oprogramowanie w coraz większym stopniu opiera się na składnikach mających formę niezależnych i samoopisujących się pakietów funkcji. Kluczem są tutaj właściwości, metody i zdarzenia dostarczanie przez składniki. Składniki mają swoje atrybuty, które zapewniają informacje deklaratywne, a także obejmują dokumentację. C# udostępnia architekturę, która bezpośrednio obsługuje to podejście, dzięki czemu język ten pozwala w bardzo naturalny sposób na tworzenie i używanie składników oprogramowania.

C# ma również bardzo pomocne funkcje do tworzenia niezawodnych i trwałych aplikacji. Funkcja ***odzyskiwania pamięci***służy do automatycznego odzyskiwania pamięci zajmowanej przez nieosiągalne i nieużywane obiekty. Funkcja ***obsługi wyjątków*** umożliwia przechwytywanie i obsługiwanie błędów. Natomiast funkcja ***bezpiecznego*** projektu języka uniemożliwia odczyt niezainicjowane zmiennych, indeksowanie tablic poza ich zakresem lub wykonywanie rzutowania na siebie nieznanych typów.

C# korzysta z ***ujednoliconego systemu typów***. Wszystkie typy w tym języku, w tym typy podstawowe takie jak `int` czy `double`, dziedziczą z jednego typu głównego typu `object`. W rezultacie wszystkie typy dzielą między sobą ten sam zestaw metod, a wartości dowolnego typu można zapisywać, przesyłać i wykorzystywać w jednolity sposób. C# obsługuje też typy odwołań i wartości zdefiniowanych przez użytkownika, co pozwala na dynamiczną alokację obiektów, a także na wbudowane przechowywanie uproszczonych struktur.

Aby upewnić C# się, że programy i biblioteki mogą się rozwijać w czasie w zgodnym zakresie, przeznaczenie ma duże znaczenie C#w projekcie ***wersji*** . W wielu językach programowania jest mało uwagi na ten problem, a w efekcie programy w tych językach są częściej częściej niż to konieczne, gdy są wprowadzane nowsze wersje bibliotek zależnych. C#Zagadnienia dotyczące projektu, które miały bezpośredni wpływ na wersje, obejmują oddzielność `virtual` i `override` modyfikatory, reguły rozpoznawania przeciążania metod oraz obsługę jawnych deklaracji elementów członkowskich interfejsu.

## <a name="hello-world"></a>Hello, World

„Hello, World” to program używany tradycyjnie jako wprowadzenie do języka programowania. Poniżej przedstawiono jego wersję w C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Pliki źródłowe C# zazwyczaj mają rozszerzenie `.cs`. Zakładając, że program „Hello, World” jest zapisany w pliku `hello.cs`, program można skompilować przy użyciu wiersza polecenia:

```console
csc hello.cs
```

Powoduje to utworzenie pliku wykonywalnego o nazwie hello.exe. Dane wyjściowe wygenerowane przez tę aplikację po jej uruchomieniu to:

```console
Hello, World
```

> [!IMPORTANT]
> Polecenie `csc` przeprowadza kompilację dla pełnej struktury i może być niedostępne na niektórych platformach.

Program „Hello, World” rozpoczyna się od dyrektywy `using`, która odwołuje się do przestrzeni nazw `System`. Przestrzenie nazw zapewniają hierarchiczny sposób organizowania programów i bibliotek C#. Zawierają one typy i inne przestrzenie nazw — np. przestrzeń nazw `System` zawiera wiele typów (takich jak klasa `Console`, do której odwołuje się program) i wiele innych przestrzeni nazw, takich jak `IO` czy `Collections`. Dyrektywa `using` odwołująca się do danej przestrzeni nazw umożliwia niekwalifikowane korzystanie z typów, które są składowymi tej przestrzeni nazw. Dzięki skorzystaniu z dyrektywy `using` program może użyć polecenia `Console.WriteLine` jako skrótu dla `System.Console.WriteLine`.

Klasa `Hello` zadeklarowa przez program „Hello, World” zawiera jedną składową, którą jest metoda o nazwie `Main`. Metoda `Main` jest deklarowana za pomocą modyfikatora statycznego. Podczas gdy metody wystąpień mogą odwoływać się do konkretnego wystąpienia obiektu otaczającego przy użyciu słowa kluczowego `this`, metody statyczne działają bez odwoływania się do konkretnego obiektu. Zgodnie z konwencją, metoda statyczna o nazwie `Main` służy jako punkt wejścia programu.

Dane wyjściowe programu są generowane przez metodę `WriteLine` klasy `Console` w przestrzeni nazw `System`. Ta klasa jest zawarta w bibliotekach klas standardowych, które domyślnie są automatycznie dołączane do kompilatora.

Aby dowiedzieć się więcej o języku C#,  zapoznaj się z poniższymi tematami zawierającymi ogólne omówienie jego elementów. Znajdziesz w nich nie tylko podstawowy opis wszystkich elementów języka C#, ale także bardziej rozbudowane informacje pozwalające na poszerzenie wiedzy.

- [Struktura programu](program-structure.md)
  - Poznaj kluczowe koncepcje organizacyjne w C# języku: ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***.
- [Typy i zmienne](types-and-variables.md)
  - Dowiedz się więcej o ***typach wartości***, ***typach referencyjnych***, i ***zmiennych*** w języku C#.
- [Wyrażenia](expressions.md)
  - ***Wyrażenia*** są tworzone przy użyciu ***operandów*** (argumentów operacji) i ***operatorów***. Wyrażenia zwracają wartość.
- [Instrukcje](statements.md)
  - ***Instrukcje*** służą do przekazywania programowi informacji o tym, co ma on wykonać.
- [Klasy i obiekty](classes-and-objects.md)
  - ***Klasy*** są najbardziej podstawowym typem w języku C#. ***Obiekty*** są wystąpieniami klasy. Klasy są tworzone przy użyciu ***składowych***, które także opisano w tym temacie.
- [Struktury](structs.md)
  - ***Struktury*** to struktury danych, które (w przeciwieństwie do klas) są typami wartości.
- [Tablice](arrays.md)
  - ***Tablica*** to struktura danych zawierająca pewną liczbę zmiennych, do których dostęp jest uzyskiwany za pomocą obliczonych indeksów.
- [Interfejsy](interfaces.md)
  - ***Interfejs*** definiuje kontrakt, który może być zaimplementowany przez klasy i struktury. Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory. Interfejs nie dostarcza implementacji elementów członkowskich, które definiuje — tylko określa elementy członkowskie, które muszą być dostarczone przez klasy lub struktury, które implementują interfejs.
- [Wyliczenia](enums.md)
  - ***Typ wyliczeniowy*** to odrębny typ wartości zawierający zestaw nazwanych stałych.
- [Delegaty](delegates.md)
  - ***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach, ale w przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.
- [Atrybuty](attributes.md)
  - ***Atrybuty*** umożliwiają programom określanie dodatkowych informacji deklaratywnych na temat typów, składników i innych jednostek.

> [!div class="step-by-step"]
> [Next](program-structure.md)
