---
title: 'Instrukcje: Zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: c3c7d350132ee6c891633141fc5c4b280989e77f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934358"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Instrukcje: Zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)

Możesz użyć `My.Application.Log` i `My.Log` obiektów można zapisać informacji o zdarzeniach występujących w aplikacji. W tym przykładzie pokazano, jak Konfigurowanie odbiornika dziennika zdarzeń tak `My.Application.Log` zapisuje informacje śledzenia do dziennika zdarzeń aplikacji.

Nie można zapisać w dzienniku zabezpieczeń. Aby można było zapisać w dzienniku systemu, musi być członkiem konta systemu lokalnego lub administratora.

Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).

### <a name="to-add-and-configure-the-event-log-listener"></a>Aby dodać i skonfigurować odbiornika dziennika zdarzeń

1. Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.

    \- lub —

    Jeśli nie ma żadnego pliku app.config

    1. Na **projektu** menu, wybierz **Dodaj nowy element**.

    2. Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.

    Znajdziesz `<listeners>` sekcji `<source>` sekcję atrybut name "DefaultSource", który jest zagnieżdżony w `<system.diagnostics>` sekcję, co jest zagnieżdżony w najwyższego poziomu `<configuration>` sekcji.

3. Dodaj ten element, do którego `<listeners>` sekcji:

    ```xml
    <add name="EventLog"/>
    ```

4. Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.

5. Dodaj ten element, do którego `<sharedListeners>` sekcji:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Zastąp `APPLICATION_NAME` z nazwą aplikacji.

    > [!NOTE]
    > Zazwyczaj aplikacja zapisuje tylko błędy w dzienniku zdarzeń. Więcej informacji o filtrowaniu dane wyjściowe dziennika, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

### <a name="to-write-event-information-to-the-event-log"></a>Aby zapisać informacje o zdarzeniach w dzienniku zdarzeń

- Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metodę, aby zapisywać informacje w dzienniku zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [jak: Rejestrowania wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

    Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu, odbiera wszystkie komunikaty powodujące `My.Application.Log` zapisuje z tego zestawu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: Rejestruje wyjątki](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
