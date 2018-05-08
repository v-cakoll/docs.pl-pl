---
title: 'Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: a62e1e8f6112a96935ce165e42d34c57b223cd95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)
Można użyć `My.Application.Log` i `My.Log` obiektów można zapisać informacji o zdarzeniach występujących w aplikacji. W tym przykładzie pokazano, jak skonfigurować odbiornik dziennika zdarzeń tak `My.Application.Log` zapisuje informacje śledzenia w dzienniku zdarzeń aplikacji.  
  
 Nie można zapisać dziennika zabezpieczeń. W celu zapisu do dziennika systemu, użytkownik musi należeć do konta systemu lokalnego lub administratora.  
  
 Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).  
  
> [!NOTE]
>  Dzienniki zdarzeń nie są obsługiwane w systemie Windows 95, Windows 98 lub Windows Millennium Edition.  
  
### <a name="to-add-and-configure-the-event-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika zdarzeń  
  
1.  Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     \- lub -  
  
     Jeśli plik app.config, nie istnieje  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Zlokalizuj `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.  
  
     Można znaleźć `<listeners>` sekcji `<source>` sekcji o atrybut name "DefaultSource", która jest zagnieżdżona w obszarze `<system.diagnostics>` sekcję, co jest zagnieżdżony najwyższego poziomu `<configuration>` sekcji.  
  
3.  Dodaj ten element, do którego `<listeners>` sekcji:  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
5.  Dodaj ten element, do którego `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Zastąp `APPLICATION_NAME` z nazwą aplikacji.  
  
    > [!NOTE]
    >  Zwykle aplikacja zapisuje tylko błędy w dzienniku zdarzeń. Więcej informacji o filtrowaniu wpisu w dzienniku, zobacz [wskazówki: filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### <a name="to-write-event-information-to-the-event-log"></a>Aby zapisać informacje dotyczące zdarzenia w dzienniku zdarzeń  
  
-   Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metody, aby zapisać informacje w dzienniku zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: zapisu komunikaty dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [porady: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu odbiera wszystkie wiadomości, które `My.Applcation.Log` zapisuje z tego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
