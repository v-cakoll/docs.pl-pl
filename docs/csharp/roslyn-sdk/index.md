---
title: Zestaw SDK platformy kompilatora .NET (interfejsy API Roslyn)
description: Dowiedz się, jak używać zestawu SDK .NET Compiler Platform (zwanego również interfejsami API Roslyn) w celu zrozumienia kodu platformy .NET, błędów w programie i naprawienia tych błędów.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: 3a202d977237ce716e3f8c0cf906894efd02196d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346953"
---
# <a name="the-net-compiler-platform-sdk"></a>Zestaw SDK .NET Compiler Platform

Kompilatory tworzą szczegółowy model kodu aplikacji, ponieważ weryfikują składnię i semantykę tego kodu. Używają tego modelu do kompilowania plików wyjściowych z kodu źródłowego. Zestaw SDK .NET Compiler Platform zapewnia dostęp do tego modelu. W coraz większym stopniu korzystamy z funkcji zintegrowanego środowiska programistycznego (IDE), takich jak IntelliSense, Refaktoryzacja, inteligentna zmiana nazwy, "Znajdź wszystkie odwołania" i "przejdź do definicji", aby zwiększyć produktywność. Korzystamy z narzędzi analizy kodu, aby poprawić jakość kodu i generatory kodu pomocne w konstruowaniu aplikacji. Ponieważ narzędzia te stają się inteligentniejsze, muszą mieć dostęp do większej i większej liczby modeli, które są tworzone tylko przez kompilatory, gdy przetwarzają kod aplikacji. Jest to podstawowa misja interfejsów API Roslyn: otwieranie czarnych pól i Zezwalanie narzędzi i użytkownikom końcowym na bogactwo informacji o kodzie.
Zamiast nieprzezroczysty kod źródłowy — w przypadku tłumaczeń kodu obiektów i interfejsów, za pomocą Roslyn, kompilatory stają się platformami: API, których można użyć do zadań związanych z kodem w narzędziach i aplikacjach.

## <a name="net-compiler-platform-sdk-concepts"></a>Pojęcia dotyczące .NET Compiler Platform SDK

Zestaw .NET Compiler Platform SDK znacząco obniży barierę do wprowadzenia do tworzenia narzędzi i aplikacji ukierunkowanych na kod. Tworzy wiele możliwości innowacji w obszarach, takich jak meta-programowanie, generowanie kodu i przekształcanie, interaktywne użycie języków C# i Visual Basic oraz osadzanie C# i Visual Basic w językach specyficznych dla domeny.

Zestaw .NET Compiler Platform SDK umożliwia tworzenie ***analizatorów*** i ***poprawek kodu*** , które wyszukują i poprawiają błędy kodowania. ***Analizatory*** wiedzą składnię i strukturę kodu oraz wykrywają praktyki, które należy skorygować. ***Poprawki kodu*** zawierają jedną lub więcej sugerowanych poprawek do obsługi błędów kodowania znalezionych przez analizatory. Zwykle Analizator i powiązane poprawki kodu są pakowane razem w jednym projekcie.

Analizatory i poprawki kodu używają statycznej analizy do zrozumienia kodu. Nie uruchamiają kodu ani nie zapewniają innych korzyści z testowania. Mogą jednak wskazywać praktyki, które często prowadzą do błędów, nieobsługiwanego kodu lub standardowej weryfikacji podstawowej.

Zestaw SDK .NET Compiler Platform zawiera pojedynczy zestaw interfejsów API, które umożliwiają badanie i zrozumienie kodu bazowej C# lub Visual Basic. Ze względu na to, że można użyć tej pojedynczej bazy kodu, można łatwiej pisać analizatory i poprawki kodu, wykorzystując składnię i interfejsy API analizy semantyki dostarczone przez zestaw SDK .NET Compiler Platform. Zwolniony z dużego zadania replikowania analizy wykonanej przez kompilator, można skoncentrować się na bardziej skoncentrowanym zadaniu wyszukiwania i rozwiązywania typowych błędów kodowania dla projektu lub biblioteki.

Mniejsza korzyść polega na tym, że analizatory i poprawki kodu są mniejsze i używają znacznie mniejszej ilości pamięci w przypadku załadowania do programu Visual Studio, jeśli zapisałeś własną bazę kodu w celu zrozumienia kodu w projekcie. Wykorzystując te same klasy, które są używane przez kompilator i program Visual Studio, można utworzyć własne statyczne narzędzia do analizy. Oznacza to, że zespół może używać analizatorów i poprawek kodu bez zauważalnego wpływu na wydajność IDE.

Istnieją trzy główne scenariusze pisania analizatorów i poprawki kodu:

1. [*Wymuś standardy kodowania zespołów*](#enforce-team-coding-standards)
1. [*Zapewnianie wskazówek dotyczących pakietów bibliotecznych*](#provide-guidance-with-library-packages)
1. [*Podaj ogólne wskazówki*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Wymuś standardy kodowania zespołów

Wiele zespołów ma standardy kodowania, które są wymuszane przez przeglądy kodu z innymi członkami zespołu. Analizatory i poprawki kodu mogą znacznie zwiększyć efektywność tego procesu. Przeglądy kodu są wykonywane, gdy deweloper udostępni swoją współpracę innym członkom zespołu. Deweloper zainwestował cały czas wymagany do ukończenia nowej funkcji przed uzyskaniem jakichkolwiek komentarzy. Tygodnie mogą wystąpić, gdy deweloper wzmacnia zwyczajy, które nie pasują do praktyk zespołu.

Analizatory są uruchamiane w postaci kodu zapisu dla deweloperów. Deweloper otrzymuje natychmiastową opinię, która zachęca do natychmiastowego zaleceń. Deweloper kompiluje zwyczajy, aby pisać zgodny kod zaraz po rozpoczęciu tworzenia prototypów. Gdy ta funkcja jest gotowa do przeglądu, wszystkie standardowe wskazówki zostały wymuszone.

Zespoły mogą tworzyć analizatory i poprawki kodu, które szukają najbardziej typowych praktyk, które naruszają metody tworzenia kodu zespołu. Można je zainstalować na komputerze dewelopera, aby wymusić standardy.

## <a name="provide-guidance-with-library-packages"></a>Zapewnianie wskazówek dotyczących pakietów bibliotecznych

Istnieją wiele bibliotek dostępnych dla deweloperów platformy .NET w oprogramowaniu NuGet.
Niektóre z nich pochodzą od firmy Microsoft, niektórych od innych firm i od członków społeczności. Te biblioteki uzyskają więcej rozwiązań i wyższe oceny, gdy deweloperzy mogą pomyślnie korzystać z tych bibliotek.

Oprócz dostarczania dokumentacji można udostępniać analizatory i poprawki kodu, które wyszukują i poprawiają typowe źle używane biblioteki. Te natychmiastowe poprawki ułatwią deweloperom szybsze przechodzenie.

Analizatory i poprawki kodu można spakować z biblioteką programu NuGet. W tym scenariuszu każdy deweloper instalujący pakiet NuGet również zainstaluje pakiet analizatora. Wszyscy deweloperzy korzystający z biblioteki natychmiast uzyskają wskazówki od zespołu w formie natychmiastowej opinii na temat błędów i sugerowanych poprawek.

## <a name="provide-general-guidance"></a>Podaj ogólne wskazówki

Społeczność deweloperów platformy .NET wykryła wzorce środowiskowe, które dobrze się sprawdzają, i najlepiej unikać wzorców. Kilku członków społeczności utworzy analizatory, które wymuszają te zalecane wzorce. Dowiesz się więcej na temat nowych pomysłów.

Te analizatory mogą być przekazywane do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) i pobierane przez deweloperów przy użyciu programu Visual Studio. Informacje o języku i platformie umożliwiają szybkie uczenie się i efektywne osiąganie zaakceptowanych praktyk. W miarę jak są one szeroko używane, Wspólnota przyjmuje te praktyki.

## <a name="next-steps"></a>Następne kroki

Zestaw SDK .NET Compiler Platform zawiera najnowsze modele obiektów języka do generowania, analizy i refaktoryzacji kodu. Ta sekcja zawiera omówienie pojęć związanych z zestawem SDK .NET Compiler Platform. Więcej informacji można znaleźć w sekcjach przewodników Szybki Start, przykłady i samouczki.

Więcej informacji o pojęciach dotyczących zestawu SDK .NET Compiler Platform można znaleźć w następujących pięciu tematach:

- [Eksplorowanie kodu za pomocą wizualizatora składni](syntax-visualizer.md)
- [Omówienie modelu interfejsu API kompilatora](compiler-api-model.md)
- [Korzystanie ze składni](work-with-syntax.md)
- [Korzystanie z semantyki](work-with-semantics.md)
- [Korzystanie z obszaru roboczego](work-with-workspace.md)

Aby rozpocząć, musisz zainstalować **zestaw SDK .NET compiler platform**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
