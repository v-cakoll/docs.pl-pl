---
title: 'Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 54169f1133ed4f77026c4332493a7b5f4532aec0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583284"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji. W tym przykładzie pokazano, jak za pomocą metody `My.Application.Log.WriteEntry` rejestrować informacje o śledzeniu do pliku dziennika.

### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika plików

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     \- lub-

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź sekcję `<listeners>` w pliku konfiguracyjnym aplikacji.

     Sekcja \<listeners >a znajduje się w sekcji \<source > z atrybutem Name "DefaultSource", który jest zagnieżdżony w sekcji \<system. Diagnostics >, która jest zagnieżdżona w obszarze \<configuration najwyższego poziomu > Paragraf.

3. Dodaj ten element do `<listeners>` sekcji:

    ```xml
    <add name="FileLogListener" />
    ```

4. Znajdź sekcję `<sharedListeners>` w sekcji `<system.diagnostics>` zagnieżdżoną w sekcji `<configuration>` najwyższego poziomu.

5. Dodaj ten element do `<sharedListeners>` sekcji:

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     Zmień wartość atrybutu `customlocation` na katalog dziennika.

    > [!NOTE]
    > Aby ustawić wartość właściwości odbiornika, Użyj atrybutu, który ma taką samą nazwę jak właściwość, z wszystkimi literami w nazwie małymi literami. Na przykład atrybuty `location` i `customlocation` ustawiają wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości.

### <a name="to-write-event-information-to-the-file-log"></a>Aby zapisać informacje o zdarzeniu w dzienniku plików

Użyj metody `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` w celu zapisania informacji w dzienniku plików. Aby uzyskać więcej informacji, zobacz [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po skonfigurowaniu odbiornika dziennika plików dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisu z tego zestawu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
