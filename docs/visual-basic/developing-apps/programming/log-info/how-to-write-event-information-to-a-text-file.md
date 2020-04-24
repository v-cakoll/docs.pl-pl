---
title: 'Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352070"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji. Ten przykład pokazuje, `My.Application.Log.WriteEntry` jak używać metody do rejestrowania informacji o śledzeniu w pliku dziennika.

### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika plików

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     \-oraz

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij pozycję **Add** (Dodaj).

2. Znajdź `<listeners>` sekcję w pliku konfiguracyjnym aplikacji.

     W \<sekcji> \<źródłowej znajdują się> detektory z atrybutem Name "DefaultSource", który jest zagnieżdżony w sekcji \<system. Diagnostics>, która jest zagnieżdżona w sekcji> konfiguracji najwyższego poziomu \<.

3. Dodaj ten element do tej `<listeners>` sekcji:

    ```xml
    <add name="FileLogListener" />
    ```

4. Znajdź `<sharedListeners>` sekcję w `<system.diagnostics>` sekcji zagnieżdżoną w sekcji najwyższego poziomu. `<configuration>`

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
    > Aby ustawić wartość właściwości odbiornika, Użyj atrybutu, który ma taką samą nazwę jak właściwość, z wszystkimi literami w nazwie małymi literami. `location` Na przykład atrybuty `customlocation` i ustawiają wartości właściwości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>

### <a name="to-write-event-information-to-the-file-log"></a>Aby zapisać informacje o zdarzeniu w dzienniku plików

Użyj metody `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` , aby zapisać informacje w dzienniku plików. Aby uzyskać więcej informacji, zobacz [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po skonfigurowaniu odbiornika dziennika plików dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
