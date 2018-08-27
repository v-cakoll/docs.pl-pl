---
title: Platforma kompilatora .NET (interfejsy API Roslyn) SDK
description: Dowiedz się, za pomocą SDK platformy kompilatora .NET (nazywane również interfejsy API Roslyn) zrozumieć kod platformy .NET, wykrywać błędy i Rozwiąż te błędy.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: 4fb67b1d7ff963a01696ce163fdcef0b7944dcee
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925034"
---
# <a name="the-net-compiler-platform-sdk"></a>Zestaw SDK platformy kompilatora .NET

Kompilatory tworzyć szczegółowy model kodu aplikacji, jak sprawdzają poprawność składnia i semantyka tego kodu. Używają tego modelu do tworzenia pliku wykonywalnego dane wyjściowe z kodu źródłowego. Zestaw SDK platformy kompilatora .NET zapewnia dostęp do tego modelu. Coraz częściej, możemy polegać na funkcje środowiska (IDE) zintegrowanego rozwoju takich jak funkcja IntelliSense, Refaktoryzacja, inteligentne rename "Znajdź wszystkie odwołania" i "Przejdź do definicji" zwiększyć naszą produktywność. Polegamy narzędzi analizy kodu w celu ulepszania swojego jakość kodu i generatorów kodu, aby ułatwić budowy aplikacji. Jak uzyskuj tych narzędzi, potrzebować dostępu do coraz więcej modelu, który tylko kompilatory tworzyć zgodnie z ich przetwarzanie kodu aplikacji. Jest to misję podstawowe interfejsy API Roslyn: otwarcie czarne skrzynki narzędzi i użytkownikom końcowym udostępnianie w szeregu informacji kompilatory się o naszego kodu.
Zamiast nieprzezroczystości źródła code w i obiektu kodu komentarz tłumaczy przy użyciu platformy Roslyn, kompilatory stają się platform: interfejsy API, które służy do zadań związanych z kodu, narzędzia i aplikacje.

## <a name="net-compiler-platform-sdk-concepts"></a>Pojęcia dotyczące zestawu SDK platformy kompilatora .NET

Zestaw SDK platformy kompilatora .NET znacznie zmniejsza barierę do tworzenia kodu, które skupia się narzędzia i aplikacje. Tworzy wiele możliwości do innowacji w obszarach, takich jak meta-programowania, generowanie kodu i transformacji, interaktywne korzystanie z języków C# i VB i osadzanie języka C# i VB w języki specyficzne dla domeny.

Zestaw SDK platformy kompilatora .NET umożliwia tworzenie ***analizatory*** i ***poprawki kodu*** , Znajdź i poprawiaj błędy kodowania. ***Analizatory*** poznać składnię i struktury kodu i wykrywanie praktyk, które powinny zostać poprawione. ***Poprawki kodu*** Podaj co najmniej jeden z sugerowanymi poprawkami adresowania kodowania błędów znalezionych przez analizatory. Zazwyczaj analizator i poprawki kodu skojarzone są dostarczane razem w jednym projekcie. 

Analizatory i poprawki kodu należy użyć analizy statycznej, aby zrozumieć kod. Nie uruchomić lub inne zalety testowania. Mogą one jednak punktu rozwiązania, które często prowadzić do błędów, kodu trudnego w utrzymaniu lub sprawdzania poprawności standardowych wytycznych.

Zestaw SDK platformy kompilatora .NET zawiera jeden zestaw interfejsów API, które pozwalają zbadać i zrozumienie kodu C# lub Visual Basic. Ponieważ można użyć tego pojedynczą bazą kodu, można napisać analizatory i poprawek kodu, aby łatwiej dzięki wykorzystaniu syntaktyczna i semantyczna analiza interfejsów API dostarczonych przez zestaw SDK platformy kompilatora .NET. Zwolniona z dużych zadanie analizy wykonywanego przez kompilator replikacji, możesz skoncentrować się na bardziej ukierunkowaną zadań znajdowania i naprawiania typowych błędów kodowania dla projektu lub biblioteki.

Korzyści z mniejszych jest swoje analizatory i poprawki kodu są mniejsze i zużywać znacznie mniej pamięci po załadowaniu w programie Visual Studio, niż ich czy jeśli napiszesz własne bazy kodu w celu zrozumienie kodu w projekcie. Korzystając z tych samych klas, które są używane przez kompilator i programu Visual Studio, możesz utworzyć własne narzędzia do analizy statycznej. Oznacza to, zespół może wykorzystać analizatory i poprawki kodu, bez zauważalnego wpływu na wydajność środowiska IDE.

Istnieją trzy główne scenariusze dotyczące pisania analizatory i poprawki kodu:

1. [*Wymuszanie norm kodowania w ramach zespołu*](#enforce-team-coding-standards)
1. [*Zapewnić wskazówki dotyczące pakietów biblioteki*](#provide-guidance-with-library-packages)
1. [*Podaj ogólne wskazówki dotyczące kodowania*](#provide-general-coding-guidance)

## <a name="enforce-team-coding-standards"></a>Wymuszanie norm kodowania w ramach zespołu

Wiele zespołów mają standardy, które są wymuszane za pomocą przeglądów kodu z innymi członkami zespołu kodowania. Analizatory i poprawki kodu ułatwia ten proces znacznie bardziej wydajne. Przeglądy kodu się zdarzyć, gdy deweloper udostępnia swoją pracę z innymi osobami w zespole. Deweloper zainwestowali będzie cały czas potrzebne do ukończenia nową funkcję, zanim uzyska wszelkie komentarze. Tygodni może przechodzą dewelopera wzmacnia nawyków, które nie są zgodne z zespołu rozwiązań.

Analizatory Uruchom jako deweloper pisze kod. Deweloper pobiera natychmiastowe informacje zwrotne, które wspiera następujące wskazówki od razu. Deweloper opracowuje nawyki do pisania kodu zgodne, tak szybko, jak oni rozpocząć tworzenie prototypów. Gdy funkcja jest gotowa dla ludzi przejrzeć, została wymuszona standardowych wytycznych.

Zespoły mogą tworzyć analizatory i poprawek kodu tego wygląd na potrzeby najbardziej typowych praktyk, które naruszają zespołu kodowania. Mogą być instalowane na komputerze Każdy deweloper, aby wymuszanie standardów.

## <a name="provide-guidance-with-library-packages"></a>Zapewnić wskazówki dotyczące pakietów biblioteki

Brak dostępnych szeregu bibliotek dla deweloperów platformy .NET dla narzędzia NuGet.
Niektóre z tych pochodzą od firmy Microsoft, niektóre z innych firm i innych członków społeczności i ochotników. Te biblioteki otrzymaj więcej przyjęcia i przeglądy wyższe, gdy deweloperzy mogą zostać obsłużone za pomocą tych bibliotek.

Oprócz zapewniania dokumentacji, można podać analizatory i poprawki kodu, które znaleźć i naprawić najczęstsze zastosowania niewłaściwa biblioteki. Te korekty natychmiastowego pomoże deweloperom powiedzie się szybciej. 

Można spakować analizatory i poprawek kodu za pomocą biblioteki dla narzędzia NuGet. W tym scenariuszu Każdy deweloper, który instaluje pakiet NuGet zainstaluje pakiet analizatora. Wszystkich deweloperów przy użyciu biblioteki natychmiast Uzyskaj wskazówki od członków zespołu w postaci natychmiastowej opinii na temat błędów i sugerowanych poprawek.

## <a name="provide-general-guidance"></a>Ogólne wytyczne

Odnalezione społeczności deweloperów platformy .NET przy użyciu wzorców środowisko, które dobrze działają i wzorce, które są najlepiej unikać. Kilka członków społeczności utworzono analizatorów, które wymuszają zaczną zalecane. Jak możemy dowiedzieć się więcej, jest zawsze miejsce na nowe pomysły.

Te analizatory mogą być przekazywane [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) i pobrany przez deweloperów używających programu Visual Studio. Nowe do języka i platformy szybko poznać akceptowane rozwiązania i stają się produktywności w podróży .NET. Ponieważ te staną się bardziej powszechnie używane, społeczności przyjmuje tych rozwiązań.

## <a name="next-steps"></a>Następne kroki

W zestawie SDK platformy kompilatora .NET zawiera najnowsze modele obiektów języka dla generowania kodu, analizy i refaktoryzacji. Ta sekcja zawiera omówienie pojęć dotyczących zestawu SDK platformy kompilatora .NET. Więcej szczegółowych informacji można znaleźć w sekcjach przewodników Szybki Start, przykładami i samouczkami.

Możesz dowiedzieć się więcej o koncepcjach w zestawie SDK platformy kompilatora .NET w tych tematach cztery:

 - [Eksplorowanie kodu za pomocą wizualizatora składni](syntax-visualizer.md)
 - [Omówienie modelu interfejsu API kompilatora](compiler-api-model.md)
 - [Korzystanie ze składni](work-with-syntax.md)
 - [Korzystanie z semantyki](work-with-semantics.md)
 - [Korzystanie z obszaru roboczego](work-with-workspace.md)
 
Aby rozpocząć pracę, musisz zainstalować **zestawu SDK platformy kompilatora .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
