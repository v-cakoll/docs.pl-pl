---
title: Przewodnik po języku C# — Przewodnik po językach C#
description: Nowy w C#? Poznaj podstawy języka.
ms.date: 02/26/2020
ms.openlocfilehash: bf5a200f2ee777698ae8564f348ffc117d9abab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79156847"
---
# <a name="a-tour-of-the-c-language"></a>Przewodnik po języku C#

C# (wymawiane "Zobacz Sharp") jest nowoczesny, zorientowanych obiektowo i typu bezpieczne języka programowania. C# ma swoje korzenie w rodzinie języków C i będzie natychmiast znane programistom C, C++, Java i JavaScript.

Ten przewodnik zawiera przegląd głównych składników języka w języku C# 8 i wcześniejszych. Jeśli chcesz eksplorować język za pomocą interaktywnych przykładów, wypróbuj wprowadzenie do samouczków [języka C#.](../tutorials/intro-to-csharp/index.md)

C# jest językiem obiektowym, ale C# dodatkowo zawiera obsługę programowania ***zorientowanego na składniki.*** Współczesny projekt oprogramowania w coraz większym stopniu opiera się na komponentach oprogramowania w postaci samodzielnych i samoopisujących się pakietów funkcjonalności. Kluczem do takich składników jest, że przedstawiają model programowania z właściwości, metody i zdarzenia. Mają atrybuty, które dostarczają deklaratywnych informacji o składniku. Zawierają one własną dokumentację. C# zawiera konstrukcje języka do obsługi bezpośrednio tych pojęć, dzięki czemu C# języka naturalnego, w którym do tworzenia i używania składników oprogramowania.

Kilka funkcji C# funkcji pomocy w budowie niezawodnych i trwałych aplikacji. ***Wyrzucanie elementów bezużytecznych*** automatycznie odzyskuje pamięć zajmowaną przez nieosiągalne nieużywane obiekty. ***Obsługa wyjątków*** zapewnia ustrukturyzowane i rozszerzalne podejście do wykrywania i odzyskiwania błędów. ***Typ-safe*** projektowania języka uniemożliwia odczytywanie ze zmiennych niezainicjowanych, indeks tablice poza ich granicami lub do wykonywania niezaznaczone rzutowania typu.

C# ma ***ujednolicony system typów***. Wszystkie typy Języka C#, w `int` tym `double`typy pierwotne, `object` takie jak i , dziedziczą z jednego typu głównego. W związku z tym wszystkie typy mają zestaw typowych operacji, a wartości dowolnego typu mogą być przechowywane, transportowane i obsługiwane w spójny sposób. Ponadto C# obsługuje zarówno typy odwołań zdefiniowanych przez użytkownika, jak i typy wartości, umożliwiając dynamiczną alokację obiektów, a także magazyn w wierszu lekkich struktur.

Aby upewnić się, że programy c# i biblioteki mogą ewoluować w czasie w sposób zgodny, duży nacisk został położony na ***przechowywanie wersji*** w projekcie Języka C#. Wiele języków programowania nie zwraca uwagi na ten problem. W rezultacie programy napisane w tych innych językach przerywają częściej niż jest to konieczne, gdy wprowadzane są nowsze wersje bibliotek zależnych. Aspekty projektu Języka C#, które były bezpośrednio pod wpływem `virtual` `override` zagadnień dotyczących wersji obejmują oddzielne i modyfikatory, reguły rozpoznawania przeciążenia metody i obsługę jawnych deklaracji elementów członkowskich interfejsu.

W nowszych wersjach C# objął inne paradygmaty programowania. C# zawiera funkcje, które obsługują funkcjonalne techniki programowania, takie jak wyrażenia lambda. Inne nowe funkcje obsługują oddzielanie danych i algorytmów, takich jak dopasowywanie wzorców.

## <a name="hello-world"></a>Witaj świecie

Program "Hello, World" jest tradycyjnie używany do wprowadzania języka programowania. Tutaj jest w Języku C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Pliki źródłowe języka C# `.cs`zazwyczaj mają rozszerzenie pliku . Aby utworzyć ten program, najpierw pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download). Następnie wykonaj polecenie, `dotnet new console -o hello` aby utworzyć nowy program i skrypt kompilacji. Program i skrypt kompilacji `Program.cs` są `hello.csproj`w plikach i , odpowiednio. Tworzenie i uruchamianie aplikacji `run` za pomocą poleceń:

```dotnetcli
cd hello
dotnet run
```

Program generuje następujące dane wyjściowe:

```console
Hello, World!
```

Program "Hello, World" rozpoczyna `using` się od `System` dyrektywy, która odwołuje się do obszaru nazw. Przestrzenie nazw zapewniają hierarchiczny sposób organizowania programów i bibliotek języka C#. Przestrzenie nazw zawierają typy i inne `System` obszary nazw — na przykład obszar `Console` nazw zawiera wiele typów, takich jak klasa, `IO` do `Collections`której odwołuje się program, oraz szereg innych obszarów nazw, takich jak i . Dyrektywa, `using` która odwołuje się do danego obszaru nazw umożliwia niekwalifikowane użycie typów, które są członkami tego obszaru nazw. Ze względu `using` na dyrektywę, `Console.WriteLine` program może `System.Console.WriteLine`używać jako skrót dla .

Klasa `Hello` zadeklarowana przez program "Hello, World" ma jeden `Main`element członkowski, metodę o nazwie . Metoda `Main` jest zadeklarowana za pomocą modyfikatora statycznego. Podczas gdy metody wystąpienia można odwoływać się `this`do określonego otaczającego wystąpienia obiektu przy użyciu słowa kluczowego , metody statyczne działają bez odwoływania się do określonego obiektu. Zgodnie z konwencją `Main` metoda statyczna o nazwie służy jako punkt wejścia programu.

Dane wyjściowe programu są tworzone `WriteLine` metodą `Console` klasy w `System` przestrzeni nazw. Ta klasa jest dostarczana przez biblioteki klas standardowych, które domyślnie są automatycznie odwoływane przez kompilator.

## <a name="elements-of-the-c-language"></a>Elementy języka C#

Jest o wiele więcej, aby dowiedzieć się więcej o C#. Poniższe tematy zawierają przegląd elementów języka Języka C#. Przeglądy te dostarczają podstawowych informacji na temat wszystkich elementów języka i dają informacje niezbędne do głębszego nurkowania:

- [Struktura programu](program-structure.md)
  - Poznaj kluczowe pojęcia organizacyjne w języku Języka C#: ***programy***, ***przestrzenie nazw,*** ***typy***, ***elementy członkowskie***i ***zestawy***.
- [Typy i zmienne](types-and-variables.md)
  - Dowiedz się więcej o ***typach wartości,*** ***typach odwołań***i ***zmiennych*** w języku C#.
- [Wyrażenia](expressions.md)
  - ***Wyrażenia*** są zbudowane z ***operandów*** i ***operatorów.*** Wyrażenia generują wartość.
- [Instrukcje](statements.md)
  - ***Instrukcje*** są używane do wyrażania działań programu.
- [Klasy i obiekty](classes-and-objects.md)
  - ***Klasy*** są najbardziej podstawowe typy C#. ***Obiekty*** są wystąpieniami klasy. Klasy są tworzone przy użyciu ***elementów członkowskich***, które są również omówione w tym temacie.
- [Tablice](arrays.md)
  - ***Tablica*** jest strukturą danych, która zawiera szereg zmiennych, które są dostępne za pośrednictwem indeksów obliczeniowych.
- [Interfejsy](interfaces.md)
  - ***Interfejs*** definiuje kontrakt, który może być implementowany przez klasy i struktury. Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory. Interfejs nie zapewnia implementacje elementów członkowskich definiuje — określa jedynie elementy członkowskie, które muszą być dostarczane przez klasy lub struktury, które implementują interfejs.
- [Delegaty](delegates.md)
  - ***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i typem zwracanym. Delegaci umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazywane jako parametry. Delegatów są podobne do koncepcji wskaźników funkcji znaleźć w niektórych innych językach, ale w przeciwieństwie do wskaźników funkcji, delegatów są zorientowane obiektowe i bezpieczne dla typu.
- [Atrybuty](attributes.md)
  - ***Atrybuty*** umożliwiają programom określenie dodatkowych informacji deklaratywnych o typach, elementach członkowskich i innych jednostkach.
  
> [!NOTE]
> Te artykuły dotyczą Języka C# 7.0 i nowszych. Niektóre funkcje mogą nie być dostępne we wcześniejszych wersjach.

> [!div class="step-by-step"]
> [Dalej](program-structure.md)
