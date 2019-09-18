---
title: Wydajność środowiska .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e58c7b3ce134139950de54d98b590ec2e6b0f3de
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046456"
---
# <a name="net-framework-performance"></a>Wydajność środowiska .NET Framework
Jeśli chcesz tworzyć aplikacje o doskonałej wydajności, należy zaprojektować i zaplanować wydajność tak samo jak w przypadku projektowania dowolnej innej funkcji aplikacji. Za pomocą narzędzi dostarczonych przez firmę Microsoft można mierzyć wydajność aplikacji oraz, w razie potrzeby, wprowadzać ulepszenia w zakresie użycia pamięci, przepływności kodu i czas odpowiedzi. W tym temacie wymieniono narzędzia analizy wydajności zapewniane przez firmę Microsoft oraz linki do innych tematów, które obejmują wydajność poszczególnych obszarów tworzenia aplikacji.  
  
## <a name="designing-and-planning-for-performance"></a>Projektowanie i planowanie wydajności  
 Jeśli potrzebujesz doskonałej aplikacji, musisz zaprojektować wydajność w aplikacji tak samo jak w przypadku każdej innej funkcji. Należy określić scenariusze krytyczne dla wydajności w aplikacji, ustawić cele wydajnościowe i zmierzyć wydajność dla tych scenariuszy aplikacji wczesne i często. Ponieważ każda aplikacja różni się od siebie i ma inne ścieżki wykonywania o kluczowym znaczeniu, co pozwala na wczesne Określanie tych ścieżek i skoncentrowanie się na założeniach, można zmaksymalizować produktywność.  
  
 Nie musisz już znać platformy docelowej w celu utworzenia aplikacji o wysokiej wydajności. Należy jednak opracować informacje o tym, które części platformy docelowej są kosztowne pod względem wydajności. Można to zrobić przez zmierzenie wydajności na początku procesu tworzenia.  
  
 Aby określić obszary, które mają kluczowe znaczenie dla wydajności i ustalić cele wydajności, należy zawsze rozważyć środowisko użytkownika. Czas uruchamiania i szybkość odpowiedzi są dwa kluczowe obszary, które mają wpływ na postrzeganie aplikacji przez użytkownika. Jeśli aplikacja korzysta z dużej ilości pamięci, może być niezależna od użytkownika lub mieć wpływ na inne aplikacje działające w systemie lub w niektórych przypadkach może to spowodować niepowodzenie procesu tworzenia sklepu Windows lub Windows Phone. Ponadto, jeśli określisz, które części kodu są wykonywane częściej, możesz upewnić się, że te fragmenty kodu są dobrze zoptymalizowane.  
  
## <a name="analyzing-performance"></a>Analizowanie wydajności  
 W ramach ogólnego planu rozwoju można ustawić punkty podczas opracowywania, gdzie będzie mierzona wydajność aplikacji i porównać wyniki z celami ustawionymi wcześniej. Zmierz swoją aplikację w środowisku i sprzęcie, które oczekują od użytkowników. Analizując wydajność aplikacji wczesne i często można zmienić decyzje dotyczące architektury, które byłyby kosztowne i kosztowne do późniejszego naprawienia w cyklu programowania. W poniższych sekcjach opisano narzędzia do oceny wydajności, za pomocą których można analizować aplikacje i omawiać śledzenie zdarzeń, które są używane przez te narzędzia.  
  
### <a name="performance-tools"></a>Narzędzia wydajności  
 Poniżej przedstawiono niektóre narzędzia do oceny wydajności, z których można korzystać w przypadku aplikacji .NET Framework.  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Analiza wydajności programu Visual Studio|Służy do analizowania użycia procesora .NET Framework aplikacji, które zostaną wdrożone na komputerach z systemem operacyjnym Windows.<br /><br /> To narzędzie jest dostępne z menu **Debuguj** w programie Visual Studio po otwarciu projektu. Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](/visualstudio/profiling/performance-explorer). **Uwaga:**  Podczas określania wartości Windows Phone docelowej Użyj funkcji analizy aplikacji Windows Phone (patrz następny wiersz).|  
|Analiza aplikacji Windows Phone|Służy do analizowania procesora i pamięci, szybkości transferu danych sieci, czasu reakcji aplikacji i zużycia baterii w aplikacjach Windows Phone.<br /><br /> To narzędzie jest dostępne z menu **Debuguj** dla projektu Windows Phone w programie Visual Studio po zainstalowaniu [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Aby uzyskać więcej informacji, zobacz [Profilowanie aplikacji dla Windows Phone 8](https://docs.microsoft.com/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Służy do identyfikowania problemów z wydajnością procesora i pamięci. To narzędzie używa funkcji śledzenia zdarzeń systemu Windows (ETW) i interfejsów API profilowania CLR w celu zapewnienia zaawansowanego badania pamięci i procesora, jak również informacji na temat odzyskiwania pamięci i kompilacji JIT. Aby uzyskać więcej informacji na temat korzystania z programu narzędzia PerfView, zobacz Samouczek i pliki pomocy dołączone do [samouczków wideo aplikacji, kanału 9](https://channel9.msdn.com/Series/PerfView-Tutorial)i wpisów w [blogu](https://blogs.msdn.microsoft.com/vancem/tag/perfview/).<br /><br /> Problemy związane z pamięcią znajdują się w temacie [using narzędzia PerfView for Memory rewizyjne](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analizator wydajności systemu Windows](https://www.microsoft.com/download/details.aspx?id=30652)|Służy do określania ogólnej wydajności systemu, na przykład wykorzystania pamięci i magazynu aplikacji, gdy wiele aplikacji jest uruchomionych na tym samym komputerze. To narzędzie jest dostępne w centrum pobierania w ramach zestawu do oceny i wdrażania systemu Windows (ADK) dla programu [!INCLUDE[win8](../../../includes/win8-md.md)]. Aby uzyskać więcej informacji, zobacz [Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer).|  
  
### <a name="event-tracing-for-windows-etw"></a>Śledzenie zdarzeń systemu Windows (ETW)  
 ETW to technika, która umożliwia uzyskiwanie informacji diagnostycznych dotyczących uruchamiania kodu i jest istotna dla wielu opisanych wcześniej narzędzi wydajności. System ETW tworzy dzienniki, gdy określone zdarzenia są zgłaszane przez .NET Framework aplikacje i Windows. Za pomocą funkcji ETW można dynamicznie włączać i wyłączać rejestrowanie, dzięki czemu można wykonywać szczegółowe śledzenie w środowisku produkcyjnym bez ponownego uruchamiania aplikacji. .NET Framework oferuje obsługę zdarzeń ETW, a ETW jest używana przez wiele narzędzi do profilowania i wydajności do generowania danych wydajności. Te narzędzia często włączają i wyłączają zdarzenia ETW, dlatego znane z nich. Aby zbierać informacje o wydajności określonych składników aplikacji, można użyć określonych zdarzeń funkcji ETW. Aby uzyskać więcej informacji na temat obsługi funkcji ETW w .NET Framework, zobacz [zdarzenia ETW w środowisku uruchomieniowym języka wspólnego](etw-events-in-the-common-language-runtime.md) i [zdarzenia ETW w bibliotece zadań równoległych i PLINQ](etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Wydajność przez typ aplikacji  
 Każdy typ aplikacji .NET Framework ma własne najlepsze rozwiązania, zagadnienia i narzędzia służące do oceny wydajności. Poniższa tabela zawiera linki do tematów dotyczących wydajności dla określonych typów aplikacji .NET Framework.  
  
|Typ aplikacji|Zobacz|  
|--------------|---------|  
|.NET Framework aplikacje dla wszystkich platform|[Odzyskiwanie pamięci i wydajność](../../standard/garbage-collection/performance.md)<br /><br /> [Wskazówki dotyczące wydajności](performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikacje w programie C++, C#i Visual Basic|[Najlepsze rozwiązania w zakresie wydajności dla aplikacji ze C++sklepu C#Windows przy użyciu systemów, i Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh750313%28v=win.10%29)|  
|Windows Presentation Foundation (WPF)|[Pakiet wydajności WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|ASP.NET|[Przegląd wydajności ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Buforowanie w aplikacjach .NET Framework](caching-in-net-framework-applications.md)|Opisuje techniki buforowania danych w celu zwiększenia wydajności aplikacji.|  
|[Inicjowanie z opóźnieniem](lazy-initialization.md)|Opisuje sposób inicjowania obiektów w miarę potrzeby w celu zwiększenia wydajności, szczególnie podczas uruchamiania aplikacji.|  
|[Niezawodność](reliability.md)|Zawiera informacje na temat zapobiegania asynchronicznym wyjątkom w środowisku serwera.|  
|[Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework](writing-large-responsive-apps.md)|Zawiera porady dotyczące wydajności zebrane z przepisywania kompilatorów C# i Visual Basic w kodzie zarządzanym i zawiera kilka rzeczywistych przykładów z C# kompilatora.|
