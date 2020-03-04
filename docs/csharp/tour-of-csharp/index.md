---
title: C# C# poradniku
description: Jesteś nowym C#? Poznaj podstawy języka.
ms.date: 02/26/2020
ms.openlocfilehash: 69651d6233bfaf217366be3850f6b3d9c550d8e2
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159146"
---
# <a name="a-tour-of-the-c-language"></a>Przewodnik po C# języku

C#(wymawiane "Zobacz Sharp") to nowoczesny, zorientowany obiektowo i bezpieczny dla typu język programowania. C#ma swoje elementy główne w rodzinie C i będzie od razu znane programistom języków C, C++, Java i JavaScript.

Ten przewodnik zawiera omówienie głównych składników języka w C# 8 i wcześniejszych wersjach. Jeśli chcesz poznać język za pomocą przykładów interaktywnych, wypróbuj [wprowadzenie do C# ](../tutorials/intro-to-csharp/index.md) samouczków.

C#jest językiem zorientowanym na obiekt, ale C# dodatkowo obsługuje programowanie ***zorientowane na składniki*** . Współczesny projekt oprogramowania jest coraz bardziej oparty na składnikach oprogramowania w postaci samodzielnych i samodzielnych pakietów funkcji. Kluczem do takich składników jest prezentowanie modelu programowania z właściwościami, metodami i zdarzeniami. Mają one atrybuty, które dostarczają deklaracyjne informacje o składniku. Zawierają one własną dokumentację. C#zapewnia konstrukcje języka do obsługi bezpośrednio tych koncepcji, co C# sprawia, że język naturalny, w którym można tworzyć i używać składników oprogramowania.

Niektóre C# funkcje ułatwiają tworzenie niezawodnych i trwałych aplikacji. ***Wyrzucanie elementów bezużytecznych*** automatycznie odzyskuje ilość pamięci zajętą nieosiągalnymi obiektami. ***Obsługa wyjątków*** zapewnia strukturalne i rozszerzalne podejście do wykrywania błędów i odzyskiwania. ***Bezpieczny dla typu*** projekt języka sprawia, że nie można odczytać z niezainicjowanych zmiennych, indeksować tablice poza granicami lub wykonywać rzutowania typu unchecked.

C#ma ***ujednolicony system typów***. Wszystkie C# typy, w tym typy pierwotne, takie jak `int` i `double`, dziedziczą z jednego głównego typu `object`. W związku z tym wszystkie typy używają zestawu typowych operacji, a wartości dowolnego typu mogą być przechowywane, transportowane i obsługiwane w spójny sposób. Ponadto C# obsługuje zarówno typy odwołań zdefiniowane przez użytkownika, jak i typy wartości, co umożliwia dynamiczne przydzielanie obiektów oraz przechowywanie w wierszu lekkich struktur.

Aby upewnić C# się, że programy i biblioteki mogą się rozwijać w czasie w zgodnym zakresie, przeznaczenie ma duże znaczenie C#w projekcie ***wersji*** . Wiele języków programowania znacznie nie ma uwagi na ten problem. W związku z tym programy zapisywane w innych językach są częściej niż to konieczne, gdy są wprowadzane nowsze wersje bibliotek zależnych. C#Zagadnienia dotyczące projektu, które miały bezpośredni wpływ na wersje, obejmują osobne modyfikatory `virtual` i `override`, reguły rozpoznawania przeciążenia metod i obsługę jawnych deklaracji elementów członkowskich interfejsu.

W nowszych wersjach, C# miało inne odmiany programistyczne. C#Program zawiera funkcje, które obsługują techniki programowania funkcjonalnego, takie jak wyrażenia lambda. Inne nowe funkcje obsługują oddzielanie danych i algorytmów, takich jak dopasowywanie do wzorców.

## <a name="hello-world"></a>Witaj świecie

Program "Hello, World" jest tradycyjnie używany do wprowadzania języka programowania. W tym miejscu znajduje C#się w:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

C#pliki źródłowe mają zwykle rozszerzenie pliku `.cs`. Aby utworzyć ten program, najpierw Pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download). Następnie wykonaj polecenie `dotnet new console -o hello`, aby utworzyć nowy program i skrypt kompilacji. Program i skrypt kompilacji są odpowiednio w plikach `Program.cs` i `hello.csproj`. Kompilowanie i uruchamianie aplikacji za pomocą poleceń `run`:

```console
cd hello
dotnet run
```

Program tworzy następujące dane wyjściowe: 

```console
Hello, World!
```

Program "Hello, World" rozpoczyna się od dyrektywy `using`, która odwołuje się do `System` przestrzeni nazw. Przestrzenie nazw zapewniają hierarchiczną metodę C# organizowania programów i bibliotek. Przestrzenie nazw zawierają typy i inne przestrzenie nazw — na przykład przestrzeń nazw `System` zawiera wiele typów, takich jak Klasa `Console`, do których odwołuje się program, oraz liczba innych przestrzeni nazw, takich jak `IO` i `Collections`. Dyrektywa `using`, która odwołuje się do danego obszaru nazw, umożliwia niekwalifikowane użycie typów, które są elementami członkowskimi tej przestrzeni nazw. Ze względu na `using`ą dyrektywę program może użyć `Console.WriteLine` jako skrótu dla `System.Console.WriteLine`.

Klasa `Hello` zadeklarowana przez program "Hello, World" ma jeden element członkowski, czyli metodę o nazwie `Main`. Metoda `Main` jest zadeklarowana przy użyciu modyfikatora static. Chociaż metody wystąpień mogą odwoływać się do określonego wystąpienia obiektu otaczającego za pomocą słowa kluczowego `this`, metody statyczne działają bez odwołania do określonego obiektu. Zgodnie z Konwencją metoda statyczna o nazwie `Main` służy jako punkt wejścia programu.

Dane wyjściowe programu są tworzone przez metodę `WriteLine` klasy `Console` w przestrzeni nazw `System`. Ta klasa jest udostępniana przez standardowe biblioteki klas, które domyślnie są przywoływane przez kompilator.

## <a name="elements-of-the-c-language"></a>Elementy C# języka

Dowiedz się więcej o tym, jak C#to zrobić. W poniższych tematach przedstawiono przegląd elementów C# języka. Te omówienia zapewniają podstawowe informacje o wszystkich elementach języka i udostępniają informacje niezbędne do szczegółowe się bardziej szczegółowo:

- [Struktura programu](program-structure.md)
  - Poznaj kluczowe koncepcje organizacyjne w C# języku: ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***.
- [Typy i zmienne](types-and-variables.md)
  - Dowiedz się więcej o ***typach wartości***, ***typach odwołań***i ***zmiennych*** w C# języku.
- [Wyrażenia](expressions.md)
  - ***Wyrażenia*** są zbudowane z ***argumentów operacji*** i ***operatorów***. Wyrażenia zwracają wartość.
- [Instrukcje](statements.md)
  - ***Instrukcje*** służą do wyrażenia działania programu.
- [Klasy i obiekty](classes-and-objects.md)
  - ***Klasy*** są najbardziej zasadniczymi C#typami. ***Obiekty*** są wystąpieniami klasy. Klasy są kompilowane przy użyciu ***elementów członkowskich***, które również zostały omówione w tym temacie.
- [Tablice](arrays.md)
  - ***Tablica*** to struktura danych zawierająca wiele zmiennych, do których można uzyskać dostęp za pomocą obliczanych indeksów.
- [Interfejsy](interfaces.md)
  - ***Interfejs*** definiuje kontrakt, który może być zaimplementowany przez klasy i struktury. Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory. Interfejs nie zapewnia implementacji elementów członkowskich, które definiuje — tylko określa elementy członkowskie, które muszą być dostarczone przez klasy lub struktury, które implementują interfejs.
- [Delegaci](delegates.md)
  - ***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach, ale w przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.
- [Atrybuty](attributes.md)
  - ***Atrybuty*** umożliwiają programom określenie dodatkowych informacji deklaratywnych dotyczących typów, elementów członkowskich i innych jednostek.
  
> [!NOTE]
> Te artykuły mają zastosowanie C# do 7,0 i nowszych. Niektóre funkcje mogą nie być dostępne we wcześniejszych wersjach.

> [!div class="step-by-step"]
> [Dalej](program-structure.md)
