---
title: Wydajność środowiska .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3f3d035ebf6472788e2c7d6e11cb1a39708367b
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800329"
---
# <a name="net-framework-performance"></a>Wydajność środowiska .NET Framework
Jeśli chcesz tworzyć aplikacje o bardzo dużej wydajności, należy zaprojektować i zaplanować wydajność tak samo jak projektowanie innych funkcji aplikacji. Możesz użyć narzędzi dostarczanych przez firmę Microsoft do pomiaru wydajności Twojej aplikacji i, jeśli to konieczne, poprawić wykorzystanie pamięci, przepływność kodu i czas odpowiedzi. Ten temat zawiera listę narzędzi do analizy wydajności udostępnianych przez Microsoft, i zawiera łącza do innych tematów, które obejmują wydajność dla konkretnych obszarów projektowania aplikacji.  
  
## <a name="designing-and-planning-for-performance"></a>Projektowanie i planowanie wydajności  
 Chcąc aplikacji o wielkiej wydajności, należy zaprojektować wydajność w swojej aplikacji dokładnie tak samo jak każdą inną funkcję. Powinieneś określić scenariusze wydajności krytycznych w aplikacji, ustawić cele w zakresie wydajności, i zmierzyć wydajność dla tych scenariuszy aplikacji, wcześnie i często. Ponieważ każda aplikacja jest inna i ma wydajność krytycznych wykonań różnych ścieżek, wczesne określanie tych ścieżek i skoncentrowanie wysiłków pozwalają zmaksymalizować wydajność pracy.  
  
 Nie musisz dokładnie znać platformy docelowej, żeby utworzyć aplikację wysokiej wydajności. Jednakże należy wypracować zrozumienie, które części docelowej platformy są kosztowne pod względem wydajności. Można to zrobić mierząc wydajność na wczesnym etapie procesu rozwoju.  
  
 Aby określić obszary, które mają zasadnicze znaczenie dla wydajności i ustanowić cele dotyczące wydajności, zawsze należy brać pod uwagę doświadczenia użytkownika. Czas uruchamiania i czas odpowiedzi są dwoma podstawowymi obszarami, które wpływają na postrzeganie danej aplikacji przez użytkownika. Jeśli Twoja aplikacja używa dużej ilości pamięci, może wydawać się powolna użytkownikowi lub wpływać na inne aplikacje uruchomione w systemie, lub, w niektórych przypadkach, może spowodować błędne działanie procesu przesyłania do Sklepu Windows lub Sklepu Windows Phone. Ponadto jeśli okaże się, które fragmenty kodu można wykonać częściej, możesz upewnić się, że te fragmenty kodu są również zoptymalizowane.  
  
## <a name="analyzing-performance"></a>Analizowanie wydajności  
 Jako część ogólnego planu rozwoju ustaw punkty podczas wdrażania, gdzie można będzie zmierzyć wydajności aplikacji i porównać wyniki z celami, które wcześniej określono. Zmierz swoje aplikacje w środowisku oraz sprzęcie, którego można oczekiwać od użytkowników. Przez wczesne i częste analizowanie wydajności Twojej aplikacji można zmienić decyzje architektoniczne, które później w cyklu rozwoju będą kosztowne i drogie do naprawienia. W poniższych sekcjach opisano narzędzia wydajności, używane do analizowania aplikacji i omawiania śledzenia zdarzeń, używanego przez te narzędzia.  
  
### <a name="performance-tools"></a>Narzędzia wydajności  
 Oto niektóre z narzędzi do oceny wydajności, których można używać z aplikacjami środowiska .NET Framework.  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Analiza wydajności programu Visual Studio|Użyj do analizowania użycia Procesora aplikacji .NET Framework, które zostaną wdrożone na komputerach z systemem operacyjnym Windows.<br /><br /> To narzędzie jest dostępne z menu **Debuguj** w programie Visual Studio po otwarciu projektu. Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](/visualstudio/profiling/performance-explorer). **Uwaga:**  Podczas określania wartości Windows Phone docelowej Użyj funkcji analizy aplikacji Windows Phone (patrz następny wiersz).|  
|Analiza aplikacji Windows Phone|Użyj do analizowania Procesora i pamięci, szybkość transferu danych w sieci, czasu reakcji aplikacji i zużycia baterii w aplikacjach Windows Phone.<br /><br /> To narzędzie jest dostępne z menu **Debuguj** dla projektu Windows Phone w programie Visual Studio po zainstalowaniu [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Aby uzyskać więcej informacji, zobacz [Profilowanie aplikacji dla Windows Phone 8](https://docs.microsoft.com/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Użyj do identyfikowania Procesora i problemów z wydajnością związanych z pamięcią. To narzędzie używa śledzenia zdarzeń dla systemu Windows (ETW) i profilowanie interfejsów API środowiska CLR do zapewniania zaawansowanej pamięci i dochodzeń CPU, a także informacji na temat wyrzucania elementów bezużytecznych i kompilacji JIT. Aby uzyskać więcej informacji na temat korzystania z programu narzędzia PerfView, zobacz Samouczek i pliki pomocy dołączone do [samouczków wideo aplikacji, kanału 9](https://channel9.msdn.com/Series/PerfView-Tutorial)i wpisów w [blogu](https://blogs.msdn.microsoft.com/vancem/tag/perfview/).<br /><br /> Problemy związane z pamięcią znajdują się w temacie [using narzędzia PerfView for Memory rewizyjne](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analizator wydajności systemu Windows](https://www.microsoft.com/download/details.aspx?id=30652)|Użyj, aby określić ogólną wydajność systemu, taką jak wykorzystanie magazynu i pamięć aplikacji, gdy wiele aplikacji jest uruchomionych na tym samym komputerze. To narzędzie jest dostępne w centrum pobierania w ramach zestawu do oceny i wdrażania systemu Windows (ADK) dla systemu Windows 8. Aby uzyskać więcej informacji, zobacz [Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer).|  
  
### <a name="event-tracing-for-windows-etw"></a>Śledzenie zdarzeń systemu Windows (ETW)  
 ETW jest techniką, która pozwala uzyskać informacje diagnostyczne na temat kodu uruchamiania i ma zasadnicze znaczenie dla wielu narzędzi wydajności wymienionych wcześniej. ETW tworzy dzienniki podczas wywoływania określonych zdarzeń przez system Windows i aplikacje .NET Framework. Dzięki ETW możesz włączać i wyłączać dynamiczne rejestrowanie, więc możesz wykonywać szczegółowe śledzenie w środowisku produkcyjnym, bez konieczności ponownego uruchamiania aplikacji. .NET Framework oferuje wsparcie dla zdarzeń ETW, a ETW jest używany przez wiele narzędzi do profilowania i wydajności w celu generowania danych dotyczących wydajności. Te narzędzia często włączają i wyłączają zdarzenia ETW, więc wiedza o nich jest pomocna. Określone zdarzenia ETW służą do zbierania informacji o wydajności poszczególnych składników aplikacji. Aby uzyskać więcej informacji na temat obsługi funkcji ETW w .NET Framework, zobacz [zdarzenia ETW w środowisku uruchomieniowym języka wspólnego](etw-events-in-the-common-language-runtime.md) i [zdarzenia ETW w bibliotece zadań równoległych i PLINQ](etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Wydajność przez typ aplikacji  
 Każdy typ aplikacji .NET Framework ma własną najlepszą praktykę, zagadnienia i narzędzia do oceny wydajności. Poniższa tabela zawiera łącza do tematów wydajności dla określonych typów aplikacji .NET Framework.  
  
|Typ aplikacji|Zobacz|  
|--------------|---------|  
|.NET Framework aplikacje dla wszystkich platform|[Odzyskiwanie pamięci i wydajność](../../standard/garbage-collection/performance.md)<br /><br /> [Wskazówki dotyczące wydajności](performance-tips.md)|  
|Aplikacje ze sklepu Windows 8. x zapisane C++w C#, i Visual Basic|[Najlepsze rozwiązania w zakresie wydajności dla aplikacji ze C++sklepu C#Windows przy użyciu systemów, i Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh750313%28v=win.10%29)|  
|Windows Presentation Foundation (WPF)|[Pakiet wydajności WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|Platforma ASP.NET|[Przegląd wydajności ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Buforowanie w aplikacjach .NET Framework](caching-in-net-framework-applications.md)|Opisano techniki buforowania danych w celu zwiększenia wydajności w swojej aplikacji.|  
|[Inicjowanie z opóźnieniem](lazy-initialization.md)|Zawiera opis sposobów inicjowania obiektów jako potrzebnych do zwiększenia wydajności, szczególnie przy uruchamianiu aplikacji.|  
|[Niezawodność](reliability.md)|Zawiera informacje o zapobieganiu wyjątkom asynchronicznego przetwarzania w środowisku serwera.|  
|[Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework](writing-large-responsive-apps.md)|Zawiera porady dotyczące wydajności zebrane z przepisywania kompilatorów C# i Visual Basic w kodzie zarządzanym i zawiera kilka rzeczywistych przykładów z C# kompilatora.|
