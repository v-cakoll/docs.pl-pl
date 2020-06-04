---
title: 'Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 298d6d85f8b21176b72db8e676617577eb03fada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410039"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)

Za pomocą `My.Application.Log` obiektów i można `My.Log` pisać informacje o zdarzeniach występujących w aplikacji. Ten przykład pokazuje, jak skonfigurować odbiornik dziennika zdarzeń, co spowoduje `My.Application.Log` zapisanie informacji o śledzeniu w dzienniku zdarzeń aplikacji.

Nie można zapisać w dzienniku zabezpieczeń. Aby można było zapisywać dane w dzienniku systemu, musisz być członkiem konta LocalSystem lub administratora.

Aby wyświetlić dziennik zdarzeń, można użyć **Eksplorator serwera** lub **Podgląd zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika zdarzeń

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

    \-oraz

    Jeśli nie ma pliku App. config,

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij pozycję **Dodaj**.

2. Znajdź `<listeners>` sekcję w pliku konfiguracyjnym aplikacji.

    `<listeners>`Sekcja w `<source>` sekcji ma atrybut name "DefaultSource", który jest zagnieżdżony w `<system.diagnostics>` sekcji, która jest zagnieżdżona w sekcji najwyższego poziomu `<configuration>` .

3. Dodaj ten element do tej `<listeners>` sekcji:

    ```xml
    <add name="EventLog"/>
    ```

4. Znajdź sekcję w sekcji `<sharedListeners>` `<system.diagnostics>` , w sekcji najwyższego poziomu `<configuration>` .

5. Dodaj ten element do tej `<sharedListeners>` sekcji:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Zamień `APPLICATION_NAME` na nazwę aplikacji.

    > [!NOTE]
    > Zazwyczaj aplikacja zapisuje tylko błędy w dzienniku zdarzeń. Aby uzyskać informacje o filtrowaniu danych wyjściowych dziennika, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Aby zapisać informacje o zdarzeniach w dzienniku zdarzeń

Użyj `My.Application.Log.WriteEntry` metody lub, `My.Application.Log.WriteException` Aby zapisać informacje w dzienniku zdarzeń. Aby uzyskać więcej informacji, zobacz [How to: Write log messages](how-to-write-log-messages.md) and [How to: log Exceptions](how-to-log-exceptions.md).

Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](how-to-log-exceptions.md)
- [Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md)
