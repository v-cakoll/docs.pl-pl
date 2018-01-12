---
title: Platforma kompilatora .NET SDK (Roslyn API)
description: "Dowiedz się na potrzeby .NET SDK platformy kompilatora (nazywanych również interfejsy API Roslyn) zrozumieć kodu platformy .NET, wykrywać błędy i Rozwiąż te błędy."
keywords: roslyn, analizator, poprawki kodu
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 260efa9810e6587224bddb196b4a746d15f785e2
ms.sourcegitcommit: 3fd4e718d1bac9769fe0c1dd08ca1b2323ae272b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2018
---
# <a name="the-net-compiler-platform-sdk"></a>Zestaw SDK platformy kompilatora .NET

Kompilatory kompilacji szczegółowe model kodu aplikacji, zgodnie z ich Sprawdź poprawność składni i semantyce kodu. Ten model ich używać do tworzenia pliku wykonywalnego wyjście z kodu źródłowego. Zestaw SDK platformy .NET kompilatora zapewnia dostęp do tego modelu. Coraz, możemy polegać na programowanie zintegrowane środowisko (IDE) funkcje takie jak IntelliSense, refaktoryzacji, Zmień nazwę inteligentnego, "Znajdź wszystkie odwołania" i "Przejdź do definicji" do zwiększenia produktywności naszych. Firma Microsoft korzystają z narzędzi analizy kodu do poprawy naszych jakości kodu i generatory kodu do pomocy w konstrukcji aplikacji. Zgodnie z tych narzędzi uzyskać inteligentny, należy uzyskać dostęp do coraz więcej modelu kompilatory tylko utworzyć przetwarzania kodu aplikacji. Jest to misji podstawowych interfejsów API Roslyn: otwarcia czarne pola, dzięki czemu narzędzia i użytkowników końcowych do udziału w wiele kompilatorów informacje ma temat naszego kodu.
Zamiast nieprzezroczystości źródła kodu — ruch przychodzący i obiektu kodu wychodzący tłumaczy za pośrednictwem Roslyn, kompilatory stają się platformy: interfejsów API, które służy do zadań związanych z kodu, narzędzi i aplikacji.

## <a name="net-compiler-platform-sdk-concepts"></a>Pojęcia dotyczące zestawu SDK platformy kompilatora .NET

Zestaw SDK platformy .NET kompilatora znacznie zmniejsza barierę tworzenia kodu fokus narzędzi i aplikacji. Tworzy wiele możliwości innowacji w obszarach, takich jak meta-programowania, generowanie kodu i przekształcenie interakcyjne używają w językach C# i VB i osadzania C# i VB w określonych języków domeny.

Zestawu SDK platformy kompilatora .NET umożliwia tworzenie ***analizatorów*** i ***kodu poprawki*** który znaleźć i poprawić błędy kodowania. ***Analizatory*** zrozumieć składni i struktury kodu i wykrywać rozwiązania, które powinno zostać naprawione. ***Kod poprawki*** Podaj co najmniej jeden sugerowanej poprawki dotyczące kodowania błędy znalezione przez analizatory. Zazwyczaj analyzer i poprawki skojarzony kod jednym pakiecie w jednym projekcie. 

Analizatory i poprawki kodu umożliwia analizę statyczną zrozumienie kodu. Nie wykonywania kodu lub inne zalety testowych. Mogą one jednak wskazywanie rozwiązania, które często prowadzić do usterki, kod unmaintanable lub standardowych wytycznych dotyczących sprawdzania poprawności.

Zestaw SDK platformy .NET kompilatora zawiera jeden zestaw interfejsów API, które umożliwiają badania i zrozumieć codebase C# lub Visual Basic. Ponieważ mogą używać tego pojedynczego codebase, można napisać analizatory i kod rozwiązuje się łatwiejsze dzięki wykorzystaniu analizy składni i semantyczne interfejsów API dostarczonych przez zestaw SDK platformy .NET kompilatora. Zwolniona z dużych zadań replikacji anaysis wykonywane przez kompilator, można skoncentrować się na bardziej ukierunkowaną zadanie Znajdowanie i rozwiązywanie typowych problemów programowania dla projektu lub biblioteki.

Mniejsze korzyścią jest to Twoje analizatory i poprawki kodu są mniejsze i użyj znacznie mniej pamięci po załadowaniu w programie Visual Studio, niż ich czy Jeśli wpisano własne codebase zrozumienie kodu w projekcie. Przy użyciu tej samej klasy używane przez kompilator i Visual Studio, możesz utworzyć własne narzędzia analizy statycznej. Oznacza to, zespołu można użyć analizatory i Kod poprawki bez zauważalnego wpływu na wydajność programu IDE.

Istnieją trzy główne scenariusze zapisywania analizatory i poprawki kodu:

1. [*Wymuszanie zespołu standardy kodowania*](#enforce-team-coding-standards)
1. [*Zapewnianie wskazówek w następującym z pakietami biblioteki*](#provide-guidance-with-library-packages)
1. [*Ogólne wytyczne kodowania*](#provide-general-coding-guidance)

## <a name="enforce-team-coding-standards"></a>Wymuszanie zespołu standardy kodowania

Wiele zespoły mają, kodowania standardy, które są wymuszane za pośrednictwem przeglądy kodu z innych członków zespołu. Analizatory i poprawki kodu ułatwia ten proces znacznie większą wydajność. Przeglądy kodu się zdarzyć, gdy dewelopera udziały pracy z innymi osobami w zespole. Będzie on zainwestowały wszystkich czasu wymaganego do ukończenia nową funkcję przed pobraniem wszelkie komentarze. Tygodni może przechodzą on wzmacnia zwyczaje, które nie są zgodne rozwiązania zespołu.

Analizatory Uruchom jako deweloper zajmują się pisaniem kodu. Pobiera on natychmiast uzyskuje opinie, które wspiera następujące wskazówki natychmiast. Tworzy on zwyczaje do pisania kodu zgodne, jak on rozpoczyna tworzenie prototypów. Gdy funkcja jest gotowy dla ludzi sprawdzić, standardowe wskazówki została wymuszona.

Zespoły mogą tworzyć analizatory i Kod poprawki tego Wyszukaj najbardziej typowe rozwiązania, naruszających zespołu praktyk kodowania. Mogą być instalowane na komputerze Każdy deweloper wymusić standardy.

## <a name="provide-guidance-with-library-packages"></a>Zapewnianie wskazówek w następującym z pakietami biblioteki

Brak dostępnych wiele bibliotek dla deweloperów platformy .NET na NuGet.
Niektóre z tych dostarczanych przez firmę Microsoft, niektóre z innych firm i inne od członków społeczności i ochotników. Te biblioteki Pobierz więcej przyjęcia i wyższe przeglądy, gdy deweloperzy mogą działać prawidłowo z tych bibliotek.

Oprócz zapewnienia dokumentacji, musisz podać analizatory i poprawki kodu, które odnaleźć i rozwiązać typowe zastosowania niewłaściwa biblioteki. Poprawki te natychmiastowego pomaga deweloperom szybciej powiodło się. 

Można spakować analizatory i Kod poprawki z biblioteką na NuGet. W tym scenariuszu Każdy deweloper, który instaluje pakiet NuGet zainstaluje pakiet analizatora. Wszystkich deweloperów przy użyciu biblioteki natychmiast otrzyma wskazówki z zespołem w formie natychmiast uzyskuje opinie na błędy i sugerowanych poprawek.

## <a name="provide-general-guidance"></a>Podaj ogólne wskazówki

Odnalezione przez wzorce obsługi, które działa także i wzorce, które najlepiej jest unikać społeczności deweloperów platformy .NET. Kilka członków społeczności utworzono analizatorów wymuszających zaczną zalecane. Jak możemy dowiedzieć się więcej, jest zawsze miejsce na nowe pomysły.

Te analizatory mogą być przekazywane [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) i pobrane przez deweloperów w programie Visual Studio. Nowe języka i platformy szybko informacje przyjęte zasady i wydajność w podróży .NET. Ponieważ te staną się bardziej powszechnie używane, społeczności przyjmuje następujące rozwiązania.

## <a name="next-steps"></a>Następne kroki

Zestawu SDK platformy kompilatora .NET zawiera najnowsze modele obiektów języka dla generowania kodu, analizy i refaktoryzacji. Ta sekcja zawiera omówienie zestawu SDK platformy kompilatora .NET. Dalsze szczegóły można znaleźć w sekcji poradniki Szybki Start, przykłady i samouczki.

Możesz dowiedzieć się więcej o koncepcjach w zestawie SDK platformy .NET kompilatora w tych tematach cztery:

 - [Omówienie modelu interfejsu API kompilatora](compiler-api-model.md)
 - [Korzystanie ze składni](work-with-syntax.md)
 - [Korzystanie z semantyki](work-with-semantics.md)
 - [Korzystanie z obszaru roboczego](work-with-workspace.md)

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
