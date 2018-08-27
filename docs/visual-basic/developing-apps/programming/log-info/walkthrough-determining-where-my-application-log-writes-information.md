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
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908228"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
`My.Application.Log` Obiektu można zapisać informacji do kilku odbiorniki logu. Odbiorniki logu są konfigurowane przez plik konfiguracji komputera i może zostać przesłonięta przez plik konfiguracji aplikacji. W tym temacie opisano domyślne ustawienia i jak określić ustawienia aplikacji.  
  
 Aby uzyskać więcej informacji na temat domyślnych lokalizacji danych wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Aby określić odbiorników dla obiektu My.Application.Log  
  
1.  Zlokalizuj plik konfiguracji zestawu. Tworzysz zestawu, można przejść do pliku app.config w programie Visual Studio z **Eksploratora rozwiązań**. W przeciwnym razie nazwa pliku konfiguracji jest dołączona za pomocą "config" Nazwa zestawu i znajduje się w tym samym katalogu co zestaw.  
  
    > [!NOTE]
    >  Nie każdy zestaw ma plik konfiguracji.  
  
     Plik konfiguracji jest plik XML.  
  
2.  Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajdujący się w `<sources>` sekcji. `<sources>` Sekcji znajduje się w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
     Jeśli nie istnieją następujące sekcje, a następnie skonfigurować w pliku konfiguracji komputera `My.Application.Log` dziennika odbiorników. W poniższych krokach opisano sposób określania definiuje plik konfiguracji komputera:  
  
    1.  Zlokalizuj plik machine.config komputera. Zazwyczaj znajduje się on w *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* katalogu, gdzie `SystemRoot` to nazwa katalogu systemu operacyjnego i `frameworkVersion` jest wersją [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
         Ustawienia w pliku machine.config mogą zostać zastąpione przez plik konfiguracji aplikacji.  
  
         Jeśli nie istnieją opcjonalne elementy wymienione poniżej, można je utworzyć.  
  
    2.  Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
         Jeśli te sekcje nie istnieje, a następnie `My.Application.Log` ma odbiorniki logu domyślne.  
  
3.  Znajdź <`add>` elementów w <`listeners>` sekcji.  
  
     Te elementy Dodaj odbiorniki logu o nazwie, aby `My.Application.Log` źródła.  
  
4.  Znajdź `<add>` elementy o nazwach odbiorniki logu w `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
5.  Dla wielu typów współdzielonych detektorów dane inicjowania odbiornika zawiera opis gdzie odbiornik kieruje dane:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje do pliku dziennika, jak opisano we wprowadzeniu.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje informacje w dzienniku zdarzeń komputera, które są określone przez `initializeData` parametru. Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników zapis do pliku określonego w `initializeData` parametru.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika zapisuje konsoli wiersza polecenia.  
  
    -   Uzyskać informacji o tym, gdzie innych rodzajów odbiorniki logu wpisać informacje zapoznaj się dokumentacją tego typu.  
  
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
