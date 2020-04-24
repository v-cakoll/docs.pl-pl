---
title: 'Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352047"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)

Za pomocą obiektów `My.Application.Log` i `My.Log` można pisać informacje o zdarzeniach występujących w aplikacji. Ten przykład pokazuje, jak skonfigurować odbiornik dziennika zdarzeń, co `My.Application.Log` spowoduje zapisanie informacji o śledzeniu w dzienniku zdarzeń aplikacji.

Nie można zapisać w dzienniku zabezpieczeń. Aby można było zapisywać dane w dzienniku systemu, musisz być członkiem konta LocalSystem lub administratora.

Aby wyświetlić dziennik zdarzeń, można użyć **Eksplorator serwera** lub **Podgląd zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika zdarzeń

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

    \-oraz

    Jeśli nie ma pliku App. config,

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij pozycję **Add** (Dodaj).

2. Znajdź `<listeners>` sekcję w pliku konfiguracyjnym aplikacji.

    `<listeners>` Sekcja `<source>` w sekcji ma atrybut name "DefaultSource", który jest zagnieżdżony w `<system.diagnostics>` sekcji, która jest zagnieżdżona w sekcji najwyższego poziomu `<configuration>` .

3. Dodaj ten element do tej `<listeners>` sekcji:

    ```xml
    <add name="EventLog"/>
    ```

4. Znajdź `<sharedListeners>` sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .

5. Dodaj ten element do tej `<sharedListeners>` sekcji:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Zamień `APPLICATION_NAME` na nazwę aplikacji.

    > [!NOTE]
    > Zazwyczaj aplikacja zapisuje tylko błędy w dzienniku zdarzeń. Aby uzyskać informacje o filtrowaniu danych wyjściowych dziennika, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Aby zapisać informacje o zdarzeniach w dzienniku zdarzeń

Użyj metody `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` , aby zapisać informacje w dzienniku zdarzeń. Aby uzyskać więcej informacji, zobacz [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
