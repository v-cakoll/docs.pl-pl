---
title: 'Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym'
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

Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym przykładzie `My.Application.Log.WriteEntry` pokazano, jak użyć metody do rejestrowania informacji śledzenia do pliku dziennika.

### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika plików

1. Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.

     \-lub -

     Jeśli nie ma pliku app.config:

    1. W menu **Projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Zlokalizuj sekcję `<listeners>` w pliku konfiguracji aplikacji.

     \<Odsłuchaczy> sekcji w sekcji \<> źródłowej z atrybutem nazwa "DefaultSource", który jest \<zagnieżdżony w sekcji> system.diagnostics, \<która jest zagnieżdżona w sekcji> konfiguracji najwyższego poziomu.

3. Dodaj ten element `<listeners>` do tej sekcji:

    ```xml
    <add name="FileLogListener" />
    ```

4. Znajdź `<sharedListeners>` sekcję `<system.diagnostics>` w sekcji zagnieżdżonej w sekcji najwyższego poziomu. `<configuration>`

5. Dodaj ten element `<sharedListeners>` do tej sekcji:

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     Zmień wartość atrybutu na `customlocation` katalog dziennika.

    > [!NOTE]
    > Aby ustawić wartość właściwości odbiornika, należy użyć atrybutu, który ma taką samą nazwę jak właściwość, ze wszystkimi literami w małych literach. Na przykład `location` atrybuty i `customlocation` ustawić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> i właściwości.

### <a name="to-write-event-information-to-the-file-log"></a>Aby zapisać informacje o zdarzeniach w dzienniku plików

Użyj `My.Application.Log.WriteEntry` metody `My.Application.Log.WriteException` lub do zapisywania informacji w dzienniku plików. Aby uzyskać więcej informacji, zobacz [Jak: Pisanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [jak: Rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po skonfigurowaniu odbiornika dziennika plików dla zestawu, odbiera `My.Application.Log` wszystkie komunikaty, które zapisuje z tego zestawu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Porady: wyjątki rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
