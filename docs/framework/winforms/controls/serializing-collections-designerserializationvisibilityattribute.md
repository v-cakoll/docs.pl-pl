---
title: 'Przewodnik: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fbb0715d148b443b1eca8f400e4ad43eb51fa43
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015734"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Przewodnik: Serializacja kolekcji typów standardowych

Niestandardowe kontrolki będą czasami uwidaczniać kolekcję jako właściwość. W tym instruktażu pokazano, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> jak używać klasy do kontrolowania, w jaki sposób kolekcja jest serializowana w czasie projektowania. <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Zastosowanie wartości do właściwości kolekcji gwarantuje, że właściwość zostanie zserializowana.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-a-control-with-a-serializable-collection"></a>Tworzenie kontrolki z kolekcją możliwy do serializacji

Pierwszym krokiem jest utworzenie kontrolki, która ma kolekcję z możliwością serializacji jako właściwość. Zawartość tej kolekcji można edytować za pomocą **edytora kolekcji**, do którego można uzyskać dostęp z okna **Właściwości** .

1. W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **SerializationDemoControlLib**.

2. Zmień `UserControl1` nazwę `SerializationDemoControl`na. Aby uzyskać więcej informacji, zobacz [zmiana nazwy kodu refaktoryzacji](/visualstudio/ide/reference/rename).

3. W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> właściwości na **10**.

4. <xref:System.Windows.Forms.TextBox> Umieść formant`SerializationDemoControl`w.

5. <xref:System.Windows.Forms.TextBox> Zaznacz kontrolkę. W oknie **Właściwości** ustaw następujące właściwości.

    |Właściwość|Zmień na|
    |--------------|---------------|
    |**Multiline**|`true`|
    |**Zadokuj**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**Paski przewijania**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. W **edytorze kodu**Zadeklaruj pole tablicy ciągów o nazwie `stringsValue` w. `SerializationDemoControl`

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. `Strings` Zdefiniuj Właściwość`SerializationDemoControl`w.

   > [!NOTE]
   > <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Wartość jest używana do włączania serializacji kolekcji.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.

9. Znajdź właściwość **Strings** w <xref:System.Windows.Forms.PropertyGrid> **kontenerze testów UserControl**. Wybierz właściwość **Strings** , a następnie wybierz przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio](./media/visual-studio-ellipsis-button.png)), aby otworzyć **Edytor kolekcji ciągów**.

10. Wprowadź kilka ciągów w **edytorze kolekcji ciągów**. Należy je oddzielić, naciskając klawisz **Enter** na końcu każdego ciągu. Po zakończeniu wprowadzania ciągów kliknij przycisk **OK** .

   > [!NOTE]
   > Wpisane ciągi są wyświetlane w <xref:System.Windows.Forms.TextBox>. `SerializationDemoControl`

## <a name="serialize-a-collection-property"></a>Serializacja właściwości kolekcji

Aby przetestować zachowanie serializacji formantu, należy umieścić go w formularzu i zmienić zawartość kolekcji z **Edytor kolekcji**. Możesz zobaczyć serializowany stan kolekcji, przeglądając specjalny plik projektanta, do którego **Projektant formularzy systemu Windows** emituje kod.

1. Dodaj projekt aplikacji systemu Windows do rozwiązania. Nadaj nazwę projektowi `SerializationDemoControlTest`.

2. W **przyborniku**Znajdź kartę o nazwie **składniki SerializationDemoControlLib**. Na tej karcie znajdziesz `SerializationDemoControl`. Aby uzyskać więcej informacji, [zobacz Przewodnik: Automatyczne wypełnianie przybornika składnikami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)niestandardowymi.

3. `SerializationDemoControl` Umieść w formularzu.

4. Znajdź właściwość w oknie **właściwości.** `Strings` Kliknij właściwość, a następnie kliknij![przycisk wielokropka (przycisk wielokropka (...) w okno właściwości programu Visual](./media/visual-studio-ellipsis-button.png)Studio.), aby otworzyć **Edytor kolekcji ciągów.** `Strings`

5. Wpisz kilka ciągów w **edytorze kolekcji ciągów**. Należy je oddzielić przez naciśnięcie klawisza **Enter** na końcu każdego ciągu. Po zakończeniu wprowadzania ciągów kliknij przycisk **OK** .

> [!NOTE]
> Wpisane ciągi są wyświetlane w <xref:System.Windows.Forms.TextBox>. `SerializationDemoControl`

6. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .

7. Otwórz węzeł **Form1** . Poniżej znajduje się plik o nazwie **Form1.Designer.cs** lub **Form1. Designer. vb**. Jest to plik, do którego **Projektant formularzy systemu Windows** emituje kod reprezentujący stan czasu projektowania formularza i jego formantów podrzędnych. Otwórz ten plik w **edytorze kodu**.

8. Otwórz region o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows** i Znajdź sekcję zatytułowaną **serializationDemoControl1**. Poniżej znajduje się kod reprezentujący serializowany stan kontrolki. Ciągi wpisane w kroku 5 pojawiają się w przypisaniu do `Strings` właściwości. Poniższe przykłady kodu w C# i Visual Basic pokazują kod podobny do tego, co zobaczysz, jeśli wpisano ciągi "Red", "pomarańczowy" i "żółty".

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. W **edytorze kodu**Zmień wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings` właściwości <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>na.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Skompiluj ponownie rozwiązanie i powtórz kroki 3 i 4.

> [!NOTE]
> W takim przypadku **Projektant formularzy systemu Windows** emituje brak przypisania do `Strings` właściwości.

## <a name="next-steps"></a>Następne kroki

Gdy wiesz, jak serializować kolekcję typów standardowych, rozważ integrację formantów niestandardowych w środowisku czasu projektowania. W poniższych tematach opisano sposób ulepszania integracji niestandardowych kontrolek w czasie projektowania:

- [Architektura czasu projektowania](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)

- [Omówienie serializacji projektanta](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Przewodnik: Tworzenie kontrolki Windows Forms, która wykorzystuje funkcje czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
