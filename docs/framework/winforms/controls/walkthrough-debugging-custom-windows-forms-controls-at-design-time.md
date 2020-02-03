---
title: Debuguj niestandardowe kontrolki w czasie projektowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740186"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a>Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania

Podczas tworzenia kontrolki niestandardowej często okaże się, że konieczne jest debugowanie zachowania w czasie projektowania. Jest to szczególnie ważne w przypadku tworzenia niestandardowego projektanta dla kontrolki niestandardowej. Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: Tworzenie kontrolki Windows Forms, która korzysta z funkcji czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md).

Kontrolki niestandardowe można debugować przy użyciu programu Visual Studio, podobnie jak w przypadku debugowania innych klas .NET Framework. Różnica polega na tym, że debugujesz osobne wystąpienie programu Visual Studio, na którym działa kod kontrolki niestandardowej.

## <a name="create-the-project"></a>Utwórz projekt

Pierwszym krokiem jest utworzenie projektu aplikacji. Ten projekt będzie używany do kompilowania aplikacji, która hostuje kontrolkę niestandardową.

W programie Visual Studio Utwórz projekt aplikacji systemu Windows, a następnie nadaj mu nazwę **DebuggingExample**.

## <a name="create-the-control-library-project"></a>Tworzenie projektu biblioteki formantów

1. Dodaj projekt **biblioteki formantów systemu Windows** do rozwiązania.

2. Dodaj nowy element **UserControl** do projektu DebugControlLibrary. Nadaj mu nazwę **DebugControl**.

3. W **Eksplorator rozwiązań**usuń domyślną kontrolkę projektu, usuwając plik kodu z podstawową nazwą UserControl1.

4. Skompiluj rozwiązanie.

## <a name="checkpoint"></a>Punkt kontrolny

W tym momencie będzie można zobaczyć kontrolkę niestandardową w **przyborniku**.

Aby sprawdzić postęp, Znajdź nową kartę o nazwie **DebugControlLibrary Components** i kliknij, aby ją zaznaczyć. Gdy zostanie otwarty, zobaczysz swój formant jako **DebugControl** z domyślną ikoną obok niej.

## <a name="add-a-property-to-your-custom-control"></a>Dodawanie właściwości do kontrolki niestandardowej

Aby zademonstrować, że kod kontrolki niestandardowej jest uruchomiony w czasie projektowania, należy dodać właściwość i ustawić punkt przerwania w kodzie implementującym właściwość.

1. Otwórz **DebugControl** w **edytorze kodu**. Dodaj następujący kod do definicji klasy:

    ```vb
    Private demoStringValue As String = Nothing
    <BrowsableAttribute(true)>
    Public Property DemoString() As String

        Get
            Return Me.demoStringValue
        End Get

        Set(ByVal value As String)
            Me.demoStringValue = value
        End Set

    End Property
    ```

    ```csharp
    private string demoStringValue = null;
    [Browsable(true)]
    public string DemoString
    {
        get
        {
            return this.demoStringValue;
        }
        set
        {
            demoStringValue = value;
        }
    }
    ```

2. Skompiluj rozwiązanie.

## <a name="add-your-custom-control-to-the-host-form"></a>Dodawanie kontrolki niestandardowej do formularza hosta

Aby debugować zachowanie w czasie projektowania kontrolki niestandardowej, należy umieścić wystąpienie niestandardowej klasy kontrolek w formularzu hosta.

1. W projekcie "DebuggingExample" Otwórz formularz Form1 w **Projektant formularzy systemu Windows**.

2. W **przyborniku**Otwórz kartę **składniki DebugControlLibrary** i przeciągnij wystąpienie **DebugControl** na formularz.

3. Znajdź `DemoString` właściwość niestandardową w oknie **Właściwości** . Należy pamiętać, że można zmienić jej wartość tak jak każda inna właściwość. Należy również zauważyć, że po wybraniu właściwości `DemoString`, ciąg opisu właściwości pojawia się u dołu okna **Właściwości** .

## <a name="set-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu na potrzeby debugowania w czasie projektowania

Aby debugować zachowanie w czasie projektowania kontrolki niestandardowej, należy debugować osobne wystąpienie programu Visual Studio, na którym działa kod kontrolki niestandardowej.

1. Kliknij prawym przyciskiem myszy projekt **DebugControlLibrary** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Właściwości**.

2. Na arkuszu właściwości **DebugControlLibrary** wybierz kartę **debugowanie** .

     W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny**. Będziesz debugować osobne wystąpienie programu Visual Studio, więc kliknij przycisk wielokropka (![przycisk wielokropka (...) na okno Właściwości przycisku programu Visual Studio](./media/visual-studio-ellipsis-button.png)), aby wyszukać środowisko IDE programu Visual Studio. Nazwa pliku wykonywalnego to **devenv. exe**, a jeśli została zainstalowana w lokalizacji domyślnej, jego ścieżka to *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.

3. Wybierz przycisk **OK**, aby zamknąć okno dialogowe.

4. Kliknij prawym przyciskiem myszy projekt **DebugControlLibrary** i wybierz pozycję **Ustaw jako projekt startowy** , aby włączyć tę konfigurację debugowania.

## <a name="debug-your-custom-control-at-design-time"></a>Debuguj kontrolkę niestandardową w czasie projektowania

Teraz możesz przystąpić do debugowania kontrolki niestandardowej, która jest uruchamiana w trybie projektowania. Po uruchomieniu sesji debugowania zostanie utworzone nowe wystąpienie programu Visual Studio i zostanie ono użyte do załadowania rozwiązania "DebuggingExample". Po otwarciu formularza Form1 w **projektancie formularzy**wystąpienie kontrolki niestandardowej zostanie utworzone i rozpocznie działanie.

1. Otwórz plik źródłowy **DebugControl** w **edytorze kodu** i umieść punkt przerwania w metodzie dostępu `Set` właściwości `DemoString`.

2. Naciśnij klawisz **F5** , aby rozpocząć sesję debugowania. Zostanie utworzone nowe wystąpienie programu Visual Studio. Wystąpienia można rozróżnić na dwa sposoby:

    - W wystąpieniu debugowania jest **uruchomione** słowo na pasku tytułu

    - Na wystąpieniu debugowania jest wyłączony przycisk **Start** na pasku narzędzi **debugowania**

   Punkt przerwania jest ustawiany w wystąpieniu debugowania.

3. W nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie "DebuggingExample". Możesz łatwo znaleźć rozwiązanie, wybierając pozycję **ostatnie projekty** z menu **plik** . Plik rozwiązania "DebuggingExample. sln" będzie wyświetlany jako ostatnio używany plik.

4. Otwórz formularz Form1 w **projektancie formularzy** i wybierz formant **DebugControl** .

5. Zmień wartość właściwości `DemoString`. Po zatwierdzeniu zmiany wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywanie zostaje zatrzymane w punkcie przerwania. Można wykonać jeden krok przez metodę dostępu do właściwości tak samo jak w przypadku każdego innego kodu.

6. Aby zatrzymać debugowanie, Zamknij hostowane wystąpienie programu Visual Studio lub wybierz przycisk **Zatrzymaj debugowanie** w wystąpieniu debugowania.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy można debugować niestandardowe kontrolki w czasie projektowania, istnieje wiele możliwości rozszerzania interakcji kontrolki ze środowiskiem IDE programu Visual Studio.

- Aby napisać kod, który będzie wykonywany tylko w czasie projektowania, można użyć właściwości <xref:System.ComponentModel.Component.DesignMode%2A> klasy <xref:System.ComponentModel.Component>. Aby uzyskać szczegółowe informacje, zobacz <xref:System.ComponentModel.Component.DesignMode%2A>.

- Istnieje kilka atrybutów, które można zastosować do właściwości kontrolki, aby manipulować interakcją kontrolki niestandardowej z projektantem. Te atrybuty można znaleźć w przestrzeni nazw <xref:System.ComponentModel?displayProperty=nameWithType>.

- Można napisać niestandardowy Projektant dla kontrolki niestandardowej. Zapewnia to pełną kontrolę nad doświadczeniem projektowym przy użyciu rozszerzalnej infrastruktury projektanta uwidocznionej przez program Visual Studio. Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: Tworzenie kontrolki Windows Forms, która korzysta z funkcji czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)
