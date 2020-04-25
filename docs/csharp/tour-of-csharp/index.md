---
title: Przewodnik programowania w języku C# — C#
description: Jesteś nowym w języku C#? Poznaj podstawy języka.
ms.date: 02/26/2020
ms.openlocfilehash: 7476356ceab39d5cccb6ccbeb991653f08a324ea
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141048"
---
# <a name="a-tour-of-the-c-language"></a>Przewodnik po języku C#

C# ("Zobacz Sharp") to nowoczesny, zorientowany obiektowo i bezpieczny dla typu język programowania. Język C# ma swoje elementy główne w rodzinie C i będzie od razu zaznajomiony z programistami C, C++, Java i JavaScript.

Ten przewodnik zawiera omówienie głównych składników języka w języku C# 8 i jego wcześniejszych wersjach. Jeśli chcesz poznać język za pomocą przykładów interaktywnych, wypróbuj samouczki [dotyczące języka C#](../tutorials/intro-to-csharp/index.md) .

C# jest językiem zorientowanym na obiekt, ale w języku C# jest dodatkowo obsługiwane programowanie ***zorientowane na składniki*** . Współczesny projekt oprogramowania jest coraz bardziej oparty na składnikach oprogramowania w postaci samodzielnych i samodzielnych pakietów funkcji. Kluczem do takich składników jest prezentowanie modelu programowania z właściwościami, metodami i zdarzeniami. Mają one atrybuty, które dostarczają deklaracyjne informacje o składniku. Zawierają one własną dokumentację. Język c# udostępnia konstrukcje języka do obsługi bezpośrednio tych koncepcji, co pozwala na tworzenie i używanie składników oprogramowania w języku C#.

Kilka funkcji języka C# pomaga w konstruowaniu niezawodnych i trwałych aplikacji. ***Wyrzucanie elementów bezużytecznych*** automatycznie odzyskuje ilość pamięci zajętą nieosiągalnymi obiektami. ***Obsługa wyjątków*** zapewnia strukturalne i rozszerzalne podejście do wykrywania błędów i odzyskiwania. ***Bezpieczny dla typu*** projekt języka sprawia, że nie można odczytać z niezainicjowanych zmiennych, indeksować tablice poza granicami lub wykonywać rzutowania typu unchecked.

Język C# ma ***ujednolicony system typów***. Wszystkie typy C#, w tym typy pierwotne `int` , `double`takie jak i, dziedziczą `object` z jednego typu głównego. W związku z tym wszystkie typy używają zestawu typowych operacji, a wartości dowolnego typu mogą być przechowywane, transportowane i obsługiwane w spójny sposób. Ponadto w języku C# obsługiwane są zarówno typy odwołań zdefiniowane przez użytkownika, jak i typy wartości, co umożliwia dynamiczne przydzielanie obiektów oraz przechowywanie w wierszu lekkich struktur.

Aby upewnić się, że programy i biblioteki C# mogą się rozwijać w czasie w zgodnym zakresie, znacznie przeznaczenie zostało ***umieszczone w projekcie w języku*** c#. Wiele języków programowania znacznie nie ma uwagi na ten problem. W związku z tym programy zapisywane w innych językach są częściej niż to konieczne, gdy są wprowadzane nowsze wersje bibliotek zależnych. Aspekty projektu języka C#, które miały bezpośrednio wpływ na kwestie związane z obsługą wersji, `virtual` obejmują `override` oddzielność i Modyfikatory, reguły rozpoznawania przeciążania metod oraz obsługę jawnych deklaracji elementów członkowskich interfejsu.

W nowszych wersjach język C# miał inne odmiany programistyczne. Język C# zawiera funkcje, które obsługują techniki programowania funkcjonalnego, takie jak wyrażenia lambda. Inne nowe funkcje obsługują oddzielanie danych i algorytmów, takich jak dopasowywanie do wzorców.

## <a name="hello-world"></a>Hello world

Program "Hello, World" jest tradycyjnie używany do wprowadzania języka programowania. W tym miejscu jest w języku C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Pliki źródłowe języka C# mają zwykle rozszerzenie `.cs`pliku. Aby utworzyć ten program, najpierw Pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download). Następnie wykonaj polecenie `dotnet new console -o hello` , aby utworzyć nowy program i skrypt kompilacji. Program i skrypt kompilacji są odpowiednio w plikach `Program.cs` i. `hello.csproj` Kompilowanie i uruchamianie aplikacji za pomocą `run` poleceń:

```dotnetcli
cd hello
dotnet run
```

Program tworzy następujące dane wyjściowe:

```dotnetcli
Hello, World!
```

Program "Hello, World" rozpoczyna się od `using` dyrektywy, która odwołuje `System` się do przestrzeni nazw. Przestrzenie nazw zapewniają hierarchiczny sposób organizowania programów i bibliotek w języku C#. Przestrzenie nazw zawierają typy i inne przestrzenie nazw — `System` na przykład przestrzeń nazw zawiera wiele typów, takich jak `Console` Klasa, do której odwołuje się program, oraz liczba innych przestrzeni nazw, `IO` takich `Collections`jak i. `using` Dyrektywa odwołująca się do danej przestrzeni nazw umożliwia niekwalifikowane użycie typów, które są elementami członkowskimi tej przestrzeni nazw. Ze względu `using` na dyrektywę program może użyć `Console.WriteLine` jako skrótu dla elementu `System.Console.WriteLine`.

`Hello` Klasa zadeklarowana przez program "Hello, World" ma jeden element członkowski, Metoda o nazwie `Main`. `Main` Metoda jest zadeklarowana przy użyciu modyfikatora static. Chociaż metody wystąpień mogą odwoływać się do określonego wystąpienia obiektu otaczającego za `this`pomocą słowa kluczowego, metody statyczne działają bez odwołania do określonego obiektu. Zgodnie z Konwencją metoda statyczna `Main` o nazwie służy jako punkt wejścia programu.

Dane wyjściowe programu są tworzone przez `WriteLine` metodę `Console` klasy w `System` przestrzeni nazw. Ta klasa jest udostępniana przez standardowe biblioteki klas, które domyślnie są przywoływane przez kompilator.

## <a name="elements-of-the-c-language"></a>Elementy języka C#

Istnieje wiele więcej informacji na temat języka C#. W poniższych tematach przedstawiono przegląd elementów języka C#. Te omówienia zapewniają podstawowe informacje o wszystkich elementach języka i udostępniają informacje niezbędne do szczegółowe się bardziej szczegółowo:

- [Struktura programu](program-structure.md)
  - Poznaj kluczowe koncepcje organizacyjne w języku C#: ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***.
- [Typy i zmienne](types-and-variables.md)
  - Dowiedz się więcej o ***typach wartości***, ***typach odwołań***i ***zmiennych*** w języku C#.
- [Wyrażenia](expressions.md)
  - ***Wyrażenia*** są zbudowane z ***argumentów operacji*** i ***operatorów***. Wyrażenia tworzą wartość.
- [Instrukcje](statements.md)
  - ***Instrukcje*** służą do wyrażenia działania programu.
- [Klasy i obiekty](classes-and-objects.md)
  - ***Klasy*** są najbardziej podstawą typów języka C#. ***Obiekty*** są wystąpieniami klasy. Klasy są kompilowane przy użyciu ***elementów członkowskich***, które również zostały omówione w tym temacie.
- [Tablice](arrays.md)
  - ***Tablica*** to struktura danych zawierająca wiele zmiennych, do których można uzyskać dostęp za pomocą obliczanych indeksów.
- [Interfejsy](interfaces.md)
  - ***Interfejs*** definiuje kontrakt, który może być zaimplementowany przez klasy i struktury. Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory. Interfejs nie zapewnia implementacji elementów członkowskich, które definiuje — tylko określa elementy członkowskie, które muszą być dostarczone przez klasy lub struktury, które implementują interfejs.
- [Delegaty](delegates.md)
  - ***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach, ale w przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.
- [Atrybuty](attributes.md)
  - ***Atrybuty*** umożliwiają programom określenie dodatkowych informacji deklaratywnych dotyczących typów, elementów członkowskich i innych jednostek.
  
> [!NOTE]
> Te artykuły mają zastosowanie do języka C# 7,0 i nowszych. Niektóre funkcje mogą nie być dostępne we wcześniejszych wersjach.

> [!div class="step-by-step"]
> [Dalej](program-structure.md)
