---
title: Ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: fa177fa1f07c52d900f57e5bf61c967f06203c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590936"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
`My.Application.Log` Obiektu można zapisać informacji do kilku odbiorniki dzienników. Odbiorniki logu są konfigurowane przez plik konfiguracji komputera i może zostać zastąpiona przez pliku konfiguracji aplikacji. W tym temacie opisano ustawienia domyślne i jak określić ustawienia aplikacji.  
  
 Aby uzyskać więcej informacji o domyślnych lokalizacji danych wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Aby określić odbiorników dla obiektu My.Application.Log  
  
1.  Zlokalizuj plik konfiguracji zestawu. Jeśli tworzysz zestawu, możesz uzyskać dostęp app.config w programie Visual Studio z **Eksploratora rozwiązań**. W przeciwnym razie nazwa pliku konfiguracji jest nazwą zestawu dołączony ".config" i znajduje się w tym samym katalogu co zestaw.  
  
    > [!NOTE]
    >  Nie każdy zestaw ma pliku konfiguracji.  
  
     Plik konfiguracji jest plikiem XML.  
  
2.  Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajduje się w `<sources>` sekcji. `<sources>` Sekcja znajduje się w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
     Jeśli nie istnieją następujące sekcje, a następnie skonfigurować pliku konfiguracji komputera `My.Application.Log` dziennika odbiorników. W poniższych krokach opisano sposób określania definiuje plik konfiguracji komputera:  
  
    1.  Znajdź plik machine.config komputera. Zazwyczaj znajduje się on w *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* katalogu, gdzie `SystemRoot` katalog systemu operacyjnego i `frameworkVersion` jest wersja [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
         Ustawienia w pliku machine.config może zostać przesłonięta przez pliku konfiguracji aplikacji.  
  
         Jeśli nie istnieją elementy opcjonalne wymienione poniżej, można je utworzyć.  
  
    2.  Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
         Jeśli nie istnieją tych sekcji, a następnie `My.Application.Log` ma odbiorniki logu domyślne.  
  
3.  Zlokalizuj <`add>` elementów <`listeners>` sekcji.  
  
     Odbiorniki logu nazwanego, aby dodać te elementy `My.Application.Log` źródła.  
  
4.  Zlokalizuj `<add>` elementy z nazwami odbiorniki logu w `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
5.  Dla wielu typów udostępnione obiekty nasłuchujące dane inicjowania odbiornika zawiera opis gdzie odbiornika kieruje dane:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje do pliku dziennika, zgodnie z opisem w wprowadzenie.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje informacje w dzienniku zdarzeń komputera określona przez `initializeData` parametru. Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników zapisać do pliku określonego w `initializeData` parametru.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika zapisuje do wiersza polecenia konsoli.  
  
    -   Aby dowiedzieć się, w którym innych typów odbiorniki logu zapisywać informacje zapoznaj się dokumentacją tego typu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [Zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md)  
 [Rozwiązywanie problemów: odbiorcy dzienników](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
