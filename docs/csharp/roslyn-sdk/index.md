---
title: Zestaw SDK platformy kompilatora .NET (interfejsy API Roslyn)
description: Dowiedz się, jak używać sdk platformy kompilatora .NET (nazywanego również interfejsami API Roslyn), aby zrozumieć kod .NET, błędy punktowe i naprawić te błędy.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: a1ceb1d11cf846e67be2c6558978e01133e591da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76742735"
---
# <a name="the-net-compiler-platform-sdk"></a>Zestaw SDK platformy kompilatora .NET

Kompilatory tworzą szczegółowy model kodu aplikacji, gdy sprawdzają poprawność składni i semantyki tego kodu. Używają tego modelu do tworzenia danych wyjściowych wykonywalnych z kodu źródłowego. Zestaw SDK platformy kompilatora .NET zapewnia dostęp do tego modelu. Coraz częściej polegamy na funkcjach zintegrowanego środowiska programistycznego (IDE), takich jak IntelliSense, refaktoryzacja, inteligentna zmiana nazwy, "Znajdź wszystkie odwołania" i "Przejdź do definicji", aby zwiększyć naszą produktywność. Polegamy na narzędziach do analizy kodu, aby poprawić jakość naszego kodu i generatorach kodu, aby pomóc w budowie aplikacji. Jak te narzędzia stają się inteligentniejsze, potrzebują dostępu do coraz większej liczby modeli, które tworzą tylko kompilatory podczas przetwarzania kodu aplikacji. Jest to podstawowa misja interfejsów API Roslyn: otwarcie czarnych skrzynek i umożliwienie narzędziom i użytkownikom końcowym udostępniania bogactwa kompilatorów informacji na temat naszego kodu.
Zamiast być nieprzezroczyste source-code-in i object-out tłumaczy za pośrednictwem Roslyn kompilatory stają się platformy: interfejsy API, które można użyć do zadań związanych z kodem w narzędzia chorążych i aplikacji.

## <a name="net-compiler-platform-sdk-concepts"></a>Pojęcia sdk platformy kompilatora .NET

Zestaw SDK platformy kompilatora .NET znacznie obniża barierę wejścia do tworzenia narzędzi i aplikacji zorientowanych na kod. Stwarza wiele możliwości innowacji w obszarach, takich jak meta-programowania, generowania kodu i transformacji, interaktywne użycie języków Języka C# i Visual Basic i osadzania Języka C# i Visual Basic w językach specyficznych dla domeny.

Zestaw SDK platformy kompilatora .NET umożliwia tworzenie ***analizatorów*** i ***poprawek kodu,*** które znajdują i korygują błędy kodowania. ***Analizatory*** zrozumieć składnię i strukturę kodu i wykryć praktyki, które powinny zostać poprawione. ***Poprawki kodu*** zapewniają co najmniej jedną sugerowaną poprawkę do rozwiązywania błędów kodowania znalezionych przez analizatory. Zazwyczaj analizator i skojarzone poprawki kodu są pakowane razem w jednym projekcie.

Analizatory i poprawki kodu używają analizy statycznej do zrozumienia kodu. Nie uruchamiają kodu ani nie zapewniają innych korzyści testowania. Mogą jednak wskazywać na praktyki, które często prowadzą do błędów, kodu nie do utrzymania lub standardowego naruszenia wytycznych.

Zestaw SDK platformy kompilatora .NET udostępnia pojedynczy zestaw interfejsów API, które umożliwiają badanie i zrozumienie bazy kodu języka C# lub Visual Basic. Ponieważ można użyć tej pojedynczej bazy kodu, można łatwiej pisać analizatory i poprawki kodu, korzystając z interfejsów API analizy składniowej i semantycznej dostarczonych przez zestaw SDK platformy kompilatora .NET. Uwolniony od dużego zadania replikowania analizy wykonanej przez kompilator, można skoncentrować się na bardziej ukierunkowane zadanie znajdowania i naprawiania typowych błędów kodowania dla projektu lub biblioteki.

Mniejszą zaletą jest to, że analizatory i poprawki kodu są mniejsze i zużywają znacznie mniej pamięci po załadowaniu w programie Visual Studio niż w przypadku, gdy napisałeś własną bazę kodu, aby zrozumieć kod w projekcie. Korzystając z tych samych klas używanych przez kompilator i Visual Studio, można utworzyć własne narzędzia analizy statycznej. Oznacza to, że zespół może używać analizatorów i poprawek kodu bez zauważalnego wpływu na wydajność IDE.

Istnieją trzy główne scenariusze pisania analizatorów i poprawek kodu:

1. [*Wymuszanie standardów kodowania zespołów*](#enforce-team-coding-standards)
1. [*Dostarczanie wskazówek dotyczących pakietów biblioteczne*](#provide-guidance-with-library-packages)
1. [*Podaj ogólne wskazówki*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Wymuszanie standardów kodowania zespołów

Wiele zespołów ma standardy kodowania, które są wymuszane za pomocą przeglądów kodu z innymi członkami zespołu. Analizatory i poprawki kodu mogą sprawić, że ten proces będzie znacznie bardziej wydajny. Przeglądy kodu mają miejsce, gdy deweloper udostępnia swoją pracę innym osobom w zespole. Deweloper będzie zainwestował cały czas potrzebny do ukończenia nowej funkcji przed uzyskaniem jakichkolwiek komentarzy. Tygodnie mogą mijać, podczas gdy deweloper wzmacnia nawyki, które nie pasują do praktyk zespołu.

Analizatory są uruchamiane jako deweloper pisze kod. Deweloper otrzymuje natychmiastową informację zwrotną, która zachęca do natychmiastowego spotoszeniu się ze wskazówkami. Deweloper tworzy nawyki do pisania zgodnego kodu, gdy tylko zaczną tworzyć prototypy. Gdy funkcja jest gotowa do przeglądu przez ludzi, wszystkie standardowe wskazówki zostały wymuszone.

Zespoły mogą tworzyć analizatory i poprawki kodu, które szukają najczęstszych praktyk, które naruszają praktyki kodowania zespołu. Można je zainstalować na komputerze każdego dewelopera, aby wymusić standardy.

## <a name="provide-guidance-with-library-packages"></a>Dostarczanie wskazówek dotyczących pakietów biblioteczne

Istnieje wiele bibliotek dostępnych dla deweloperów .NET na NuGet.
Niektóre z nich pochodzą od firmy Microsoft, niektóre z firm zewnętrznych, a inne od członków społeczności i wolontariuszy. Te biblioteki uzyskać więcej wdrażania i wyższe opinie, gdy deweloperzy mogą odnieść sukces z tych bibliotek.

Oprócz dostarczania dokumentacji można podać analizatory i poprawki kodu, które znajdują i korygują typowe niewłaściwe użycie biblioteki. Te natychmiastowe poprawki pomogą deweloperom szybciej odnieść sukces.

Można spakować analizatory i poprawki kodu z biblioteki na NuGet. W tym scenariuszu każdy deweloper, który instaluje pakiet NuGet zainstaluje również pakiet analizatora. Wszyscy deweloperzy korzystający z biblioteki natychmiast otrzymają wskazówki od twojego zespołu w postaci natychmiastowej informacji zwrotnej na temat błędów i sugerowanych poprawek.

## <a name="provide-general-guidance"></a>Podaj ogólne wskazówki

Społeczność deweloperów .NET została odkryta za pomocą wzorców środowiska, które działają dobrze i wzorców, których najlepiej unikać. Kilku członków społeczności utworzyło analizatory, które wymuszają zalecane wzorce. Jak dowiadujemy się więcej, zawsze jest miejsce na nowe pomysły.

Te analizatory mogą być przekazywane do [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) i pobierane przez deweloperów przy użyciu programu Visual Studio. Nowicjusze w języku i platformie szybko uczą się akceptowanych praktyk i stają się produktywni wcześniej w swojej podróży .NET. W miarę jak stają się one coraz powszechniej stosowane, wspólnota przyjmuje te praktyki.

## <a name="next-steps"></a>Następne kroki

Zestaw SDK platformy kompilatora .NET zawiera najnowsze modele obiektów języka do generowania kodu, analizy i refaktoryzacji. Ta sekcja zawiera omówienie koncepcyjne zestaw SDK platformy kompilatora .NET. Więcej szczegółów można znaleźć w sekcji przewodników Szybki start, przykłady i samouczki.

Więcej informacji na temat pojęć w zestawie SDK platformy kompilatora .NET można uzyskać w następujących pięciu tematach:

- [Eksplorowanie kodu za pomocą wizualizatora składni](syntax-visualizer.md)
- [Omówienie modelu interfejsu API kompilatora](compiler-api-model.md)
- [Korzystanie ze składni](work-with-syntax.md)
- [Korzystanie z semantyki](work-with-semantics.md)
- [Korzystanie z obszaru roboczego](work-with-workspace.md)

Aby rozpocząć, należy zainstalować **zestaw SDK platformy kompilatora .NET:**

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
