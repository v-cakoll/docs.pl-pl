---
title: 'Porady: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 297a7080b0c34fa10f976cbbbfb48d8c35786aca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458079"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Przewodnik: serializacja kolekcji typów standardowych

Niestandardowe kontrolki będą czasami uwidaczniać kolekcję jako właściwość. W tym instruktażu pokazano, jak za pomocą klasy <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> kontrolować, w jaki sposób kolekcja jest serializowana w czasie projektowania. Zastosowanie wartości <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> do właściwości kolekcji gwarantuje, że właściwość zostanie zserializowana.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: serializować kolekcje typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-a-control-with-a-serializable-collection"></a>Tworzenie kontrolki z kolekcją możliwy do serializacji

Pierwszym krokiem jest utworzenie kontrolki, która ma kolekcję z możliwością serializacji jako właściwość. Zawartość tej kolekcji można edytować za pomocą **edytora kolekcji**, do którego można uzyskać dostęp z okna **Właściwości** .

1. W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **SerializationDemoControlLib**.

2. Zmień nazwę `UserControl1` na `SerializationDemoControl`. Aby uzyskać więcej informacji, zobacz [zmiana nazwy kodu refaktoryzacji](/visualstudio/ide/reference/rename).

3. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> na **10**.

4. Umieść formant <xref:System.Windows.Forms.TextBox> w `SerializationDemoControl`.

5. Wybierz kontrolkę <xref:System.Windows.Forms.TextBox>. W oknie **Właściwości** ustaw następujące właściwości.

    |Właściwość|Zmień na|
    |--------------|---------------|
    |**Multiline**|`true`|
    |**Zadokuj**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**Paski przewijania**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. W **edytorze kodu**Zadeklaruj pole tablicy ciągów o nazwie `stringsValue` w `SerializationDemoControl`.

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. Zdefiniuj Właściwość `Strings` w `SerializationDemoControl`.

   > [!NOTE]
   > Wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> służy do włączania serializacji kolekcji.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.

9. Znajdź właściwość **Strings** w <xref:System.Windows.Forms.PropertyGrid> **kontenera testów UserControl**. Wybierz właściwość **stringss** , a następnie wybierz przycisk wielokropka (![przycisk wielokropka (...) na okno właściwości](./media/visual-studio-ellipsis-button.png)programu Visual Studio), aby otworzyć **Edytor kolekcji ciągów**.

10. Wprowadź kilka ciągów w **edytorze kolekcji ciągów**. Należy je oddzielić, naciskając klawisz **Enter** na końcu każdego ciągu. Po zakończeniu wprowadzania ciągów kliknij przycisk **OK** .

   > [!NOTE]
   > Wpisane ciągi pojawiają się w <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`.

## <a name="serialize-a-collection-property"></a>Serializacja właściwości kolekcji

Aby przetestować zachowanie serializacji formantu, należy umieścić go w formularzu i zmienić zawartość kolekcji z **Edytor kolekcji**. Możesz zobaczyć serializowany stan kolekcji, przeglądając specjalny plik projektanta, do którego **Projektant formularzy systemu Windows** emituje kod.

1. Dodaj projekt aplikacji systemu Windows do rozwiązania. Nadaj nazwę projektowi `SerializationDemoControlTest`.

2. W **przyborniku**Znajdź kartę o nazwie **składniki SerializationDemoControlLib**. Na tej karcie znajdziesz `SerializationDemoControl`. Aby uzyskać więcej informacji, zobacz [Przewodnik: automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. Umieść `SerializationDemoControl` w formularzu.

4. Znajdź Właściwość `Strings` w oknie **Właściwości** . Kliknij właściwość `Strings`, a następnie kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwościm przycisku programu Visual Studio.](./media/visual-studio-ellipsis-button.png)), aby otworzyć **Edytor kolekcji ciągów**.

5. Wpisz kilka ciągów w **edytorze kolekcji ciągów**. Należy je oddzielić przez naciśnięcie klawisza **Enter** na końcu każdego ciągu. Po zakończeniu wprowadzania ciągów kliknij przycisk **OK** .

    > [!NOTE]
    > Wpisane ciągi pojawiają się w <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`.

6. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .

7. Otwórz węzeł **Form1** . Poniżej znajduje się plik o nazwie **Form1.Designer.cs** lub **Form1. Designer. vb**. Jest to plik, do którego **Projektant formularzy systemu Windows** emituje kod reprezentujący stan czasu projektowania formularza i jego formantów podrzędnych. Otwórz ten plik w **edytorze kodu**.

8. Otwórz region o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows** i Znajdź sekcję zatytułowaną **serializationDemoControl1**. Poniżej znajduje się kod reprezentujący serializowany stan kontrolki. Ciągi wpisane w kroku 5 pojawiają się w przypisaniu do właściwości `Strings`. Poniższe przykłady kodu w C# i Visual Basic pokazują kod podobny do tego, co zobaczysz, jeśli wpisano ciągi "Red", "pomarańczowy" i "żółty".

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. W **edytorze kodu**zmień wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> właściwości `Strings` na <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Skompiluj ponownie rozwiązanie i powtórz kroki 3 i 4.

> [!NOTE]
> W takim przypadku **Projektant formularzy systemu Windows** emituje brak przypisania do właściwości `Strings`.

## <a name="next-steps"></a>Następne kroki

Gdy wiesz, jak serializować kolekcję typów standardowych, rozważ integrację formantów niestandardowych w środowisku czasu projektowania. W poniższych tematach opisano sposób ulepszania integracji niestandardowych kontrolek w czasie projektowania:

- [Architektura czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)

- [Omówienie serializacji projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
