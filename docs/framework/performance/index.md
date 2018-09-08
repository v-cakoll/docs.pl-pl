---
title: Wydajność środowiska .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59f8ceaf7981aebf3ae64e10d253004780f47e50
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208721"
---
# <a name="net-framework-performance"></a>Wydajność środowiska .NET Framework
Jeśli chcesz tworzyć aplikacje o bardzo dużej wydajności, należy zaprojektować i zaplanować wydajność tak samo jak projektowanie innych funkcji aplikacji. Można użyć narzędzi dostarczanych przez firmę Microsoft do pomiaru wydajności Twojej aplikacji i, jeśli to konieczne, poprawić wykorzystanie pamięci, przepływność kodu i szybkość reakcji. Ten temat zawiera listę narzędzi do analizy wydajności zapewnia firmy Microsoft i zawiera łącza do innych tematów, które obejmują wydajność dla konkretnych obszarów projektowania aplikacji.  
  
## <a name="designing-and-planning-for-performance"></a>Projektowanie i Planowanie wydajności  
 Chcąc aplikacji o wielkiej wydajności, należy zaprojektować wydajność w swojej aplikacji tak jak projektowanie innych funkcji. Należy określić scenariusze wydajności krytycznych w aplikacji, ustaw cele wydajności i zmierzyć wydajność dla tych scenariuszy aplikacji, wcześnie i często. Ponieważ każda aplikacja jest inna i ma inną wydajność krytycznych wykonań ścieżek, Wczesne określanie tych ścieżek i skoncentrowanie wysiłków pozwalają zmaksymalizować wydajność pracy.  
  
 Nie musisz dokładnie znać platformy docelowej, aby utworzyć aplikację wysokiej wydajności. Jednakże należy wypracować zrozumienie, które części docelowej platformy są kosztowne pod względem wydajności. Można to zrobić mierząc wydajność na wczesnym etapie procesu rozwoju.  
  
 Aby określić obszary, które mają zasadnicze znaczenie dla wydajności i ustanowić cele dotyczące wydajności, zawsze należy wziąć pod uwagę doświadczenia użytkownika. Czas uruchamiania i czas odpowiedzi są dwoma podstawowymi obszarami, które wpłyną na postrzeganie danej aplikacji przez użytkownika. Jeśli aplikacja używa dużej ilości pamięci, może występować powolna użytkownikowi lub wpływać na inne aplikacje uruchomione w systemie lub, w niektórych przypadkach może spowodować błędne proces przesyłania Windows Store lub Windows Phone Store. Ponadto jeśli okaże się, które części kodu można wykonać częściej, można upewnij się, te fragmenty kodu są również zoptymalizowane.  
  
## <a name="analyzing-performance"></a>Analizowanie wydajności  
 Częścią ogólnego planu rozwoju Ustaw punkty podczas wdrażania gdzie można będzie zmierzyć wydajności aplikacji i należy porównać wyniki z celami, które wcześniej określono. Zmierz swoje aplikacje w środowisku oraz sprzęcie, który oczekiwać od użytkowników. Przez analizowanie wydajności Twojej aplikacji, wcześnie i często można zmienić decyzje architektoniczne, które będą kosztowne i drogie do naprawienia w dalszej części cyklu tworzenia oprogramowania. W poniższych sekcjach opisano narzędzia wydajności, których można użyć do analizowania aplikacji i omawiania śledzenia zdarzeń, które jest używane przez te narzędzia.  
  
### <a name="performance-tools"></a>Narzędzia wydajności  
 Poniżej przedstawiono niektóre narzędzia wydajności, których można używać z aplikacjami środowiska .NET Framework.  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Analiza wydajności programu Visual Studio|Użyj do analizowania użycia Procesora aplikacji .NET Framework, które zostaną wdrożone na komputerach z systemem operacyjnym Windows.<br /><br /> To narzędzie jest dostępne z **debugowania** menu w programie Visual Studio po otwarciu projektu. Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](/visualstudio/profiling/performance-explorer). **Uwaga:** analiza aplikacji Windows Phone użycia (zob. następny wiersz) Jeśli Windows Phone.|  
|Analiza aplikacji Windows Phone|Użyj do analizowania Procesora i pamięci, szybkość transferu danych sieci, czas reakcji aplikacji i zużycia baterii w aplikacjach Windows Phone.<br /><br /> To narzędzie jest dostępne z **debugowania** menu dla projektu Windows Phone w programie Visual Studio po zainstalowaniu [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Aby uzyskać więcej informacji, zobacz [profilowanie aplikacji dla Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Służy do identyfikowania Procesora i problemów z wydajnością związane z pamięcią. To narzędzie używa śledzenia zdarzeń dla Windows (ETW) i środowiska CLR profilowania API, aby zapewnić zaawansowanej pamięci i dochodzeń CPU, a także informacji na temat wyrzucania elementów bezużytecznych i kompilacji JIT. Aby uzyskać więcej informacji na temat używania narzędzia PerfView, zobacz pliki samouczka i pomocy, które są dołączone do aplikacji [samouczki wideo kanału 9](http://channel9.msdn.com/Series/PerfView-Tutorial), i [wpisów w blogu](https://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> W przypadku problemów specyficznych dla pamięci zobacz [za pomocą narzędzia PerfView dla pamięci](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analizator wydajności Windows](https://www.microsoft.com/download/details.aspx?id=30652)|Użyj, aby określić ogólną wydajność systemu, takie jak wykorzystanie magazynu i pamięć aplikacji, gdy wiele aplikacji jest uruchomionych na tym samym komputerze. To narzędzie jest dostępne w Centrum pobierania jako część Windows Assessment and Deployment Kit (ADK) dla [!INCLUDE[win8](../../../includes/win8-md.md)]. Aby uzyskać więcej informacji, zobacz [Analizator wydajności Windows](https://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>Śledzenie zdarzeń dla Windows (ETW)  
 ETW jest techniką, która pozwala uzyskać informacje diagnostyczne na temat kodu uruchamiania i ma zasadnicze znaczenie dla wielu narzędzi wydajności wymienionych wcześniej. ETW tworzy dzienniki podczas wywoływania określonych zdarzeń przy użyciu aplikacji .NET Framework i Windows. Za pomocą funkcji ETW należy można włączać i wyłączać dynamiczne rejestrowanie, dzięki czemu możesz wykonywać szczegółowe śledzenie w środowisku produkcyjnym, bez konieczności ponownego uruchamiania aplikacji. .NET Framework oferuje wsparcie dla zdarzeń ETW, a ETW jest używany przez wiele narzędzi do profilowania i wydajności do generowania danych dotyczących wydajności. Te narzędzia często Włączanie i wyłączanie zdarzenia ETW, więc wiedza o nich jest pomocna. Określone zdarzenia ETW służy do zbierania informacji o poszczególnych składników wydajności aplikacji. Aby uzyskać więcej informacji na temat obsługi ETW w programie .NET Framework, zobacz [zdarzenia ETW w środowisku uruchomieniowym CLR](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) i [zdarzenia ETW w bibliotece równoległych zadań i PLINQ](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Wydajność przez typ aplikacji  
 Każdy typ aplikacji .NET Framework ma swój własny najlepsze rozwiązania, zagadnienia i narzędzia do oceny wydajności. Poniższa tabela zawiera linki do tematów wydajności dla określonych typów aplikacji .NET Framework.  
  
|Typ aplikacji|Zobacz|  
|--------------|---------|  
|Aplikacje .NET framework dla wszystkich platform|[Odzyskiwanie pamięci i wydajność](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Wskazówki dotyczące wydajności](../../../docs/framework/performance/performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje napisane w języku C++, C# i Visual Basic|[Wydajność — najlepsze rozwiązania dla aplikacji Windows Store przy użyciu języka C++, C# i Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Zagadnienia dotyczące wydajności aplikacji dla Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Analiza aplikacji Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Pobieranie aplikacji Windows Phone na rynku szybciej](https://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[Pakiet wydajności WPF](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Porady dotyczące wydajności](https://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[Przegląd wydajności platformy ASP.NET](https://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Praktyczne wskazówki do zwiększenia wydajności aplikacji w Windows Forms](https://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Buforowanie w aplikacjach .NET Framework](../../../docs/framework/performance/caching-in-net-framework-applications.md)|W tym artykule opisano techniki buforowania danych w celu zwiększenia wydajności w swojej aplikacji.|  
|[Inicjowanie z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md)|W tym artykule opisano sposób inicjowania obiektów jako potrzebnych do zwiększenia wydajności, szczególnie przy uruchamianiu aplikacji.|  
|[Niezawodność](../../../docs/framework/performance/reliability.md)|Zawiera informacje o zapobieganiu wyjątkom asynchronicznego przetwarzania w środowisku serwera.|  
|[Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework](../../../docs/framework/performance/writing-large-responsive-apps.md)|Zawiera porady dotyczące wydajności zebrane z ponownego zapisywania adresów kompilatory C# i Visual Basic w kodzie zarządzanym i zawiera kilka przykładów rzeczywistych z kompilatorem C#.|
