---
title: Tworzenie kompletnego rozwiązania .NET Core w systemie Windows, przy użyciu programu Visual Studio 2017 r.
description: Dowiedz się, jak tworzyć kompletne rozwiązanie .NET Core w Visual Studio 2017 w systemie Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.openlocfilehash: 52b8781cdc29ac776123402c982353ef437ce74f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214396"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Tworzenie kompletnego rozwiązania .NET Core w systemie Windows, przy użyciu programu Visual Studio 2017 r.

Visual Studio 2017 udostępnia środowisko deweloperskie kompletne umożliwiający projektowanie aplikacji .NET Core. Procedury przedstawione w tym dokumencie opisano kroki niezbędne do utworzenia typowe rozwiązania .NET Core, które zawiera biblioteki wielokrotnego użytku, testowania i korzystanie z bibliotek innych firm. 

## <a name="prerequisites"></a>Wymagania wstępne

Postępuj zgodnie z instrukcjami [naszą stronę wymagania wstępne](../windows-prerequisites.md) aktualizacji środowiska.

## <a name="a-solution-using-only-net-core-projects"></a>Rozwiązanie przy użyciu tylko projekty .NET Core

### <a name="writing-the-library"></a>Pisanie biblioteki

1. W programie Visual Studio, wybierz **pliku**, **nowy**, **projektu**. W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła i wybierz polecenie **.NET Standard** węzeł, a następnie wybierz pozycję **biblioteki klas (.NET Standard)**. 

2. Nazwa projektu, "Library" i "Golden" rozwiązania. Pozostaw **Utwórz katalog rozwiązania** zaznaczone. Kliknij przycisk **OK**.

3. W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.

4. Wybierz polecenie "nuget.org" jako **źródła pakietu**i wybierz polecenie **Przeglądaj** kartę. Przeglądaj w poszukiwaniu **Newtonsoft.Json**. Kliknij przycisk **zainstalować**i zaakceptuj umowę licencyjną. Pakiet powinien zostać wyświetlony w obszarze **zależności/NuGet** i automatycznie go przywrócić.

5. Zmień nazwę `Class1.cs` pliku `Thing.cs`. Zaakceptuj zmiany nazwy klasy. Dodaj metodę: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

   Rozwiązanie powinno utworzyć bez błędów.

### <a name="writing-the-test-project"></a>Zapisywanie projektu testowego

1. W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **rozwiązania** węzeł i wybierz polecenie **Dodaj**, **nowy projekt**. W **nowy projekt** okna dialogowego, w obszarze **Visual C# / .NET Core**, wybierz **jednostkowy projekt testowy (.NET Core)**. Nadaj jej nazwę na "TestLibrary", a następnie kliknij przycisk OK. 

2. W **TestLibrary** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**. Kliknij przycisk **projektów**, sprawdź projektu biblioteki i kliknij przycisk OK. Spowoduje to dodanie odwołania do biblioteki z projektu testowego.

3. Zmień nazwę `UnitTest1.cs` pliku `LibraryTests.cs` i zaakceptować zmiany nazwy klasy. Dodaj `using Library;` na początku pliku i Zamień `TestMethod1` metodę z następującym kodem:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Teraz można skompilować. 
   
4. Na **Test** menu, wybierz **Windows**, **Eksploratora testów** Aby uruchomić okno Eksploratora testów do obszaru roboczego. Po kilku sekundach `ThingGetsObjectValFromNumber` testu powinien zostać wyświetlony w Eksploratorze testów. Wybierz **uruchomić wszystkie**.
   
   Należy przekazać testu.

### <a name="writing-the-console-app"></a>Pisanie aplikacji konsoli

1. W Eksploratorze rozwiązań Otwórz menu kontekstowego dla rozwiązania, a następnie dodaj nową **aplikacji konsoli (.NET Core)** projektu. Nazwę "Aplikacja".

2. W **aplikacji** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj**, **odwołania**. 

3. W **Menedżera odwołań** dialogowym wyboru **biblioteki** w obszarze **projekty**, **rozwiązania** węzeł, a następnie kliknij przycisk **OK**

6. Otwórz menu kontekstowe dla **aplikacji** węzeł i wybierz polecenie **Ustaw jako projekt startowy**. Dzięki temu, że naciśnięcie klawisza F5 lub CTRL + F5 rozpocznie aplikacji konsoli.

7. Otwórz `Program.cs` plików, dodawanie `using Library;` dyrektywy na początku pliku, a następnie dodaj `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` do `Main` — metoda.

8. Ustaw punkt przerwania po wierszu, który właśnie został dodany.

9. Naciśnij klawisz F5, aby uruchomić aplikację.

   Aplikacja powinno utworzyć bez błędów, a powinien trafienie punktu przerwania. Należy również możliwość sprawdzenia, czy dane wyjściowe aplikacji "odpowiedź jest 42.".
