---
title: "Wydajność środowiska .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa4db0e3e136eee1d2037ad6041ac6945d313776
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-performance"></a>Wydajność środowiska .NET Framework
Jeśli chcesz utworzyć aplikacje o bardzo dużej wydajności, projektowanie i Planowanie wydajności tylko innych funkcji aplikacji czy projektu. Można używać narzędzi dostarczanych przez firmę Microsoft do mierzenia wydajności aplikacji i, w razie potrzeby poprawiają wykorzystanie pamięci, kod przepływności i czasu odpowiedzi. W tym temacie wymieniono narzędzia analizy wydajności firmy Microsoft zapewnia i łącza do innych tematów, które obejmują wydajność dla określonych obszarach tworzenia aplikacji.  
  
## <a name="designing-and-planning-for-performance"></a>Projektowanie i Planowanie wydajności  
 Jeśli chcesz wspaniałej aplikacji zostanie wykonana, należy projektować wydajności w swojej aplikacji tak samo, jak będzie projektowania innych funkcji. Wczesne i często należy określić scenariuszy o kluczowym znaczeniu wydajności w aplikacji, ustaw cele dotyczące wydajności i miar wydajności dotyczących następujących scenariuszy aplikacji. Ponieważ każdej aplikacji jest inna i ma inny wykonywania krytyczne wydajności ścieżki, wczesne określenie tych ścieżek i skupienie wysiłków umożliwiają zmaksymalizować wydajność pracy.  
  
 Nie trzeba znać całkowicie docelowej platformy do utworzenia aplikacji wysokiej wydajności. Jednak należy opracować zrozumienia części docelowej platformy jest kosztowna pod względem wydajności. Można to zrobić przez pomiaru wydajności wcześnie w procesie tworzenia aplikacji.  
  
 Określenie obszarów, które są istotne wydajności i ustanowienie cele wydajności, zawsze należy wziąć pod uwagę środowisko użytkownika. Czas uruchamiania i czas odpowiedzi są dwóch podstawowych obszarach, które wpłyną na użytkownika z punktu widzenia użytkownika aplikacji. Jeśli aplikacja korzysta z dużej ilości pamięci, może występować wolna dla użytkownika lub mieć wpływ na inne aplikacje uruchomione w systemie lub, w niektórych przypadkach można niepowodzenie procesu przesyłania Sklepu Windows lub Sklepu Windows Phone. Ponadto jeśli okaże się, które części kodu wykonania częściej, można upewnij się, że te fragmenty kodu są również zoptymalizowane pod.  
  
## <a name="analyzing-performance"></a>Analizowanie wydajności  
 W ramach ogólnego planu rozwoju Ustaw punkty podczas programowania gdzie będą mierzyć wydajność aplikacji i porównywania wyników z wcześniej określonych celów. Zmierz aplikacji w środowisku i sprzętu, na którym oczekujesz swoim użytkownikom. Za analizowanie wydajności aplikacji, wczesne i często można zmienić architektury decyzje, które mogą być kosztowne i kosztowne naprawa później w cyklu programowania. W poniższych sekcjach opisano narzędzia wydajności, których można użyć do analizowania aplikacji i śledzenie zdarzeń, który jest używany przez te narzędzia omówiono w nim.  
  
### <a name="performance-tools"></a>Narzędzia wydajności  
 Poniżej przedstawiono niektóre narzędzi wydajności, których można używać z aplikacji .NET Framework.  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Analiza wydajności programu Visual Studio|Umożliwia analizowanie użycia procesora CPU aplikacji .NET Framework, które zostanie wdrożone na komputerach z systemem systemu operacyjnego Windows.<br /><br /> To narzędzie jest dostępne z **debugowania** menu w programie Visual Studio po otwarciu projektu. Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](/visualstudio/profiling/performance-explorer). **Uwaga:** analizy aplikacji Windows Phone Użyj (zobacz następnego wiersza) gdy Windows Phone.|  
|Analiza aplikacji Windows Phone|Służy do analizowania procesora CPU i pamięci, szybkość transferu danych w sieci, czas odpowiedzi aplikacji i zużycie baterii w aplikacji Windows Phone.<br /><br /> To narzędzie jest dostępne z **debugowania** menu dla projektu Windows Phone w programie Visual Studio po zainstalowaniu [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=265773). Aby uzyskać więcej informacji, zobacz [profilowania aplikacji Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[Narzędzia PerfView](http://www.microsoft.com/download/details.aspx?id=28567)|Służy do identyfikowania Procesora i problemy z wydajnością związane z pamięcią. To narzędzie używa śledzenie zdarzeń systemu Windows (ETW) i CLR profilowania interfejsów API, aby zapewnić zaawansowane pamięci i Procesora dochodzenia, a także informacje o czyszczeniu i kompilacji JIT. Aby uzyskać więcej informacji na temat używania narzędzia PerfView Zobacz pliki samouczka i pomocy, które są dołączone do aplikacji, [samouczki wideo z witryny Channel 9](http://channel9.msdn.com/Series/PerfView-Tutorial), i [blogach](http://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Problemy dotyczące pamięci, zobacz [przy użyciu narzędzia PerfView dochodzeń pamięci](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analizator wydajności systemu Windows](http://www.microsoft.com/download/details.aspx?id=30652)|Służy do określania ogólnej wydajności systemu, takie jak pamięci oraz Magazyn aplikacji używać po wielu aplikacji uruchomionych na tym samym komputerze. To narzędzie jest dostępny z Centrum pobierania jako część systemu Windows Assessment and Deployment Kit (ADK) dla [!INCLUDE[win8](../../../includes/win8-md.md)]. Aby uzyskać więcej informacji, zobacz [Analizator wydajności systemu Windows](http://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>Śledzenie zdarzeń systemu Windows (ETW)  
 ETW to technika pozwala uzyskać informacje diagnostyczne o uruchamianiu kodu, który ma zasadnicze znaczenie dla wielu narzędzi wydajności wymienione wcześniej. ETW tworzy Dzienniki aplikacji programu .NET Framework i Windows są generowane określonego zdarzenia. Za pomocą funkcji ETW można włączyć i wyłączyć rejestrowanie dynamicznie, tak, aby można było wykonać szczegółowe śledzenie w środowisku produkcyjnym bez ponownego uruchamiania aplikacji. .NET Framework zapewnia obsługę zdarzeń ETW i ETW jest używany przez wiele narzędzi do profilowania i wydajności do wygenerowania danych dotyczących wydajności. Te narzędzia często Włączanie i wyłączanie zdarzenia ETW, więc ich znajomości jest przydatne. Określonych zdarzeń ETW służy do zbierania informacji o konkretnym składniki wydajności aplikacji. Aby uzyskać więcej informacji na temat obsługi funkcji ETW w programie .NET Framework, zobacz [zdarzenia ETW w środowisku uruchomieniowym języka](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) i [zdarzenia ETW w bibliotece równoległych zadań i PLINQ](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Wydajność przez typ aplikacji  
 Każdy typ aplikacji .NET Framework ma własną najlepszych praktyk, zagadnienia i narzędzia do oceny wydajności. Poniższe łącza tabeli do tematów wydajność dla określonych typów aplikacji .NET Framework.  
  
|Typ aplikacji|Zobacz|  
|--------------|---------|  
|Aplikacje środowiska .NET framework dla wszystkich platform|[Odzyskiwanie pamięci i wydajność](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Wskazówki dotyczące wydajności](../../../docs/framework/performance/performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikacji napisanych w języku C++, C# i Visual Basic|[Najlepsze praktyki wydajności dla aplikacji ze Sklepu Windows przy użyciu języka C++, C# i Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Zagadnienia dotyczące wydajności aplikacji Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Analiza aplikacji Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Pobierz aplikacje Windows Phone w witrynie Marketplace szybsze](http://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[Pakiet wydajności WPF](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Porady dotyczące wydajności](http://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[Omówienie wydajności programu ASP.NET](http://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Praktyczne wskazówki dotyczące zwiększania wydajności aplikacji formularzy systemu Windows](http://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Buforowanie w aplikacjach .NET Framework](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Opisuje metody do buforowania danych w celu zwiększenia wydajności w aplikacji.|  
|[Inicjowanie z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md)|Zawiera opis sposobu zainicjowania obiekty wymagane do zwiększenia wydajności, szczególnie podczas uruchamiania aplikacji.|  
|[Niezawodność](../../../docs/framework/performance/reliability.md)|Zawiera informacje dotyczące zapobiegania asynchroniczne wyjątki w środowisku serwera.|  
|[Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework](../../../docs/framework/performance/writing-large-responsive-apps.md)|Zawiera wskazówki dotyczące wydajności zebrane z ponowne zapisywanie C# i Visual Basic kompilatory w kodzie zarządzanym i zawiera kilka przykładów rzeczywistych kompilatora C#.|
