---
title: 'Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 6e83f8450ca7be8a2dcd5ff43eab3dd2ec0d2f1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410065"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)

Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o zdarzeniach występujących w aplikacji. Ten przykład pokazuje, jak używać `My.Application.Log.WriteEntry` metody do rejestrowania informacji o śledzeniu w pliku dziennika.

### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika plików

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     \-oraz

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij pozycję **Dodaj**.

2. Znajdź `<listeners>` sekcję w pliku konfiguracyjnym aplikacji.

     \<listeners>Sekcja w \<source> sekcji ma atrybut name "DefaultSource", który jest zagnieżdżony w \<system.diagnostics> sekcji, która jest zagnieżdżona w sekcji najwyższego poziomu \<configuration> .

3. Dodaj ten element do tej `<listeners>` sekcji:

    ```xml
    <add name="FileLogListener" />
    ```

4. Znajdź `<sharedListeners>` sekcję w `<system.diagnostics>` sekcji zagnieżdżoną w sekcji najwyższego poziomu `<configuration>` .

5. Dodaj ten element do tej `<sharedListeners>` sekcji:

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     Zmień wartość `customlocation` atrybutu na katalog dziennika.

    > [!NOTE]
    > Aby ustawić wartość właściwości odbiornika, Użyj atrybutu, który ma taką samą nazwę jak właściwość, z wszystkimi literami w nazwie małymi literami. Na przykład `location` `customlocation` atrybuty i ustawiają wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości i.

### <a name="to-write-event-information-to-the-file-log"></a>Aby zapisać informacje o zdarzeniu w dzienniku plików

Użyj `My.Application.Log.WriteEntry` metody lub, `My.Application.Log.WriteException` Aby zapisać informacje w dzienniku plików. Aby uzyskać więcej informacji, zobacz [How to: Write log messages](how-to-write-log-messages.md) and [How to: log Exceptions](how-to-log-exceptions.md).

Po skonfigurowaniu odbiornika dziennika plików dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](how-to-log-exceptions.md)
