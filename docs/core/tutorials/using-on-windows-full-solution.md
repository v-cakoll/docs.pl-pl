---
title: Tworzenie kompletnego rozwiązania .NET Core w Windows, przy użyciu programu Visual Studio 2017
description: Dowiedz się, jak tworzyć kompletnego rozwiązania .NET Core w programie Visual Studio 2017 na Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: b3e466511fcae447f5bb54b83f13b25bc90c6539
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296844"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Tworzenie kompletnego rozwiązania .NET Core w Windows, przy użyciu programu Visual Studio 2017

Program Visual Studio 2017 zapewnia środowisko projektowe w pełni funkcjonalne służące do tworzenia aplikacji platformy .NET Core. Procedury przedstawione w tym dokumencie opisano czynności, które są niezbędne do utworzenia typowe rozwiązania .NET Core, który zawiera biblioteki do ponownego wykorzystania, testowania i korzystanie z bibliotek innych firm. 

## <a name="prerequisites"></a>Wymagania wstępne

Postępuj zgodnie z instrukcjami [naszą stronę wymagań wstępnych](../windows-prerequisites.md) na zaktualizowanie środowiska.

## <a name="a-solution-using-only-net-core-projects"></a>Rozwiązanie z użyciem tylko w projektach .NET Core

### <a name="writing-the-library"></a>Zapisywanie w bibliotece

1. W programie Visual Studio, wybierz **pliku**, **New**, **projektu**. W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła i wybierz polecenie **.NET Standard** węzła, a następnie wybierz **biblioteki klas (.NET Standard)**. Spowoduje to utworzenie biblioteki .NET Standard, który jest przeznaczony dla platformy .NET Core oraz ewentualne innych implementacji .NET, która obsługuje wersję 2.0 [.NET Standard](../../standard/net-standard.md).

2. Nazwa projektu "Library" i "Golden" rozwiązania. Pozostaw **Utwórz katalog rozwiązania** zaznaczone. Kliknij przycisk **OK**.

3. W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.

4. Wybierz pozycję "nuget.org" jako **źródła pakietu**i wybierz polecenie **Przeglądaj** kartę. Przeglądaj w poszukiwaniu **Newtonsoft.Json**. Kliknij przycisk **zainstalować**i zaakceptuj umowę licencyjną. Pakiet powinien zostać wyświetlony w obszarze **zależności/NuGet** i automatycznie przywrócony.

5. Zmień nazwę `Class1.cs` plik `Thing.cs`. Zaakceptować zmiany nazwy klasy. Dodaj metodę: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

   Rozwiązania należy utworzyć bez błędów.

### <a name="writing-the-test-project"></a>Trwa zapisywanie projektu testowego

1. W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **rozwiązania** węzeł i wybierz polecenie **Dodaj**, **nowy projekt**. W **nowy projekt** okna dialogowego, w obszarze **Visual C# / .NET Core**, wybierz **projekt testów jednostkowych (.NET Core)**. Nadaj mu nazwę "TestLibrary", a następnie kliknij przycisk OK. 

2. W **TestLibrary** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**. Kliknij przycisk **projektów**, a następnie zaznacz projekt biblioteki i kliknij przycisk OK. Dodaje to odwołanie do biblioteki w projekcie testowym.

3. Zmień nazwę `UnitTest1.cs` plik `LibraryTests.cs` i zaakceptować zmiany nazwy klasy. Dodaj `using Library;` na początku pliku i Zastąp `TestMethod1` metoda następującym kodem:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Powinny teraz być zdolny do skompilowania rozwiązania. 
   
4. Na **Test** menu, wybierz **Windows**, **Eksploratora testów** Aby uruchomić okno Eksploratora testów do obszaru roboczego. Po kilku sekundach `ThingGetsObjectValFromNumber` test powinien zostać wyświetlony w Eksploratorze testów. Wybierz **uruchomić wszystkie**.
   
   Test powinien zakończy się pomyślnie.

### <a name="writing-the-console-app"></a>Pisanie aplikacji konsoli

1. W Eksploratorze rozwiązań Otwórz menu kontekstowe dla rozwiązania, a następnie dodaj nową **Aplikacja konsoli (.NET Core)** projektu. Nadaj mu nazwę "Aplikacja".

2. W **aplikacji** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj**, **odwołania**. 

3. W **Menadżer odwołań** okno dialogowe, sprawdź **biblioteki** w obszarze **projektów**, **rozwiązania** węzłem, a następnie kliknij przycisk **OK**

6. Otwórz menu kontekstowe dla **aplikacji** węzeł i wybierz polecenie **Ustaw jako projekt startowy**. Daje to gwarancję, że naciśnięcie F5 lub CTRL + F5 zostanie uruchomiona aplikacja konsoli.

7. Otwórz `Program.cs` Dodaj `using Library;` dyrektywę w górnej części pliku, a następnie dodaj `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` do `Main` metody.

8. Ustaw punkt przerwania po wierszu, który właśnie został dodany.

9. Naciśnij klawisz F5, aby uruchomić aplikację.

   Aplikacja powinien być kompilowany bez błędów i powinna trafiony punkt przerwania. Należy również możliwość sprawdzenia, czy dane wyjściowe aplikacji, "odpowiedź brzmi 42.".
