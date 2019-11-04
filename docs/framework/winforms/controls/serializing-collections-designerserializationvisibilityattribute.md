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
# <a name="walkthrough-serialize-collections-of-standard-types"></a><span data-ttu-id="e361b-102">Przewodnik: serializacja kolekcji typów standardowych</span><span class="sxs-lookup"><span data-stu-id="e361b-102">Walkthrough: Serialize collections of standard types</span></span>

<span data-ttu-id="e361b-103">Niestandardowe kontrolki będą czasami uwidaczniać kolekcję jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="e361b-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="e361b-104">W tym instruktażu pokazano, jak za pomocą klasy <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> kontrolować, w jaki sposób kolekcja jest serializowana w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="e361b-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="e361b-105">Zastosowanie wartości <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> do właściwości kolekcji gwarantuje, że właściwość zostanie zserializowana.</span><span class="sxs-lookup"><span data-stu-id="e361b-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="e361b-106">Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: serializować kolekcje typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="e361b-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e361b-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e361b-107">Prerequisites</span></span>

<span data-ttu-id="e361b-108">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e361b-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="e361b-109">Tworzenie kontrolki z kolekcją możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="e361b-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="e361b-110">Pierwszym krokiem jest utworzenie kontrolki, która ma kolekcję z możliwością serializacji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="e361b-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="e361b-111">Zawartość tej kolekcji można edytować za pomocą **edytora kolekcji**, do którego można uzyskać dostęp z okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="e361b-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="e361b-112">W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="e361b-112">In Visual Studio, create a Windows Control Library project, and name it **SerializationDemoControlLib**.</span></span>

2. <span data-ttu-id="e361b-113">Zmień nazwę `UserControl1` na `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-113">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="e361b-114">Aby uzyskać więcej informacji, zobacz [zmiana nazwy kodu refaktoryzacji](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="e361b-114">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="e361b-115">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> na **10**.</span><span class="sxs-lookup"><span data-stu-id="e361b-115">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to **10**.</span></span>

4. <span data-ttu-id="e361b-116">Umieść formant <xref:System.Windows.Forms.TextBox> w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-116">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="e361b-117">Wybierz kontrolkę <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e361b-117">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="e361b-118">W oknie **Właściwości** ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="e361b-118">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="e361b-119">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e361b-119">Property</span></span>|<span data-ttu-id="e361b-120">Zmień na</span><span class="sxs-lookup"><span data-stu-id="e361b-120">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="e361b-121">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="e361b-121">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="e361b-122">**Zadokuj**</span><span class="sxs-lookup"><span data-stu-id="e361b-122">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="e361b-123">**Paski przewijania**</span><span class="sxs-lookup"><span data-stu-id="e361b-123">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="e361b-124">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="e361b-124">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="e361b-125">W **edytorze kodu**Zadeklaruj pole tablicy ciągów o nazwie `stringsValue` w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-125">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="e361b-126">Zdefiniuj Właściwość `Strings` w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-126">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e361b-127">Wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> służy do włączania serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e361b-127">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="e361b-128">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="e361b-128">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="e361b-129">Znajdź właściwość **Strings** w <xref:System.Windows.Forms.PropertyGrid> **kontenera testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="e361b-129">Find the **Strings** property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="e361b-130">Wybierz właściwość **stringss** , a następnie wybierz przycisk wielokropka (![przycisk wielokropka (...) na okno właściwości](./media/visual-studio-ellipsis-button.png)programu Visual Studio), aby otworzyć **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="e361b-130">Select the **Strings** property, then select the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="e361b-131">Wprowadź kilka ciągów w **edytorze kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="e361b-131">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="e361b-132">Należy je oddzielić, naciskając klawisz **Enter** na końcu każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="e361b-132">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="e361b-133">Po zakończeniu wprowadzania ciągów kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="e361b-133">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e361b-134">Wpisane ciągi pojawiają się w <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-134">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serialize-a-collection-property"></a><span data-ttu-id="e361b-135">Serializacja właściwości kolekcji</span><span class="sxs-lookup"><span data-stu-id="e361b-135">Serialize a collection property</span></span>

<span data-ttu-id="e361b-136">Aby przetestować zachowanie serializacji formantu, należy umieścić go w formularzu i zmienić zawartość kolekcji z **Edytor kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="e361b-136">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="e361b-137">Możesz zobaczyć serializowany stan kolekcji, przeglądając specjalny plik projektanta, do którego **Projektant formularzy systemu Windows** emituje kod.</span><span class="sxs-lookup"><span data-stu-id="e361b-137">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

1. <span data-ttu-id="e361b-138">Dodaj projekt aplikacji systemu Windows do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e361b-138">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="e361b-139">Nadaj nazwę projektowi `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="e361b-139">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="e361b-140">W **przyborniku**Znajdź kartę o nazwie **składniki SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="e361b-140">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="e361b-141">Na tej karcie znajdziesz `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-141">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="e361b-142">Aby uzyskać więcej informacji, zobacz [Przewodnik: automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="e361b-142">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="e361b-143">Umieść `SerializationDemoControl` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e361b-143">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="e361b-144">Znajdź Właściwość `Strings` w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="e361b-144">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="e361b-145">Kliknij właściwość `Strings`, a następnie kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwościm przycisku programu Visual Studio.](./media/visual-studio-ellipsis-button.png)), aby otworzyć **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="e361b-145">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="e361b-146">Wpisz kilka ciągów w **edytorze kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="e361b-146">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="e361b-147">Należy je oddzielić przez naciśnięcie klawisza **Enter** na końcu każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="e361b-147">Separate them by pressing **Enter** at the end of each string.</span></span> <span data-ttu-id="e361b-148">Po zakończeniu wprowadzania ciągów kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="e361b-148">Click **OK** when you are finished entering strings.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e361b-149">Wpisane ciągi pojawiają się w <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="e361b-149">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

6. <span data-ttu-id="e361b-150">W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .</span><span class="sxs-lookup"><span data-stu-id="e361b-150">In **Solution Explorer**, click the **Show All Files** button.</span></span>

7. <span data-ttu-id="e361b-151">Otwórz węzeł **Form1** .</span><span class="sxs-lookup"><span data-stu-id="e361b-151">Open the **Form1** node.</span></span> <span data-ttu-id="e361b-152">Poniżej znajduje się plik o nazwie **Form1.Designer.cs** lub **Form1. Designer. vb**.</span><span class="sxs-lookup"><span data-stu-id="e361b-152">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="e361b-153">Jest to plik, do którego **Projektant formularzy systemu Windows** emituje kod reprezentujący stan czasu projektowania formularza i jego formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e361b-153">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="e361b-154">Otwórz ten plik w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="e361b-154">Open this file in the **Code Editor**.</span></span>

8. <span data-ttu-id="e361b-155">Otwórz region o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows** i Znajdź sekcję zatytułowaną **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="e361b-155">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="e361b-156">Poniżej znajduje się kod reprezentujący serializowany stan kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e361b-156">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="e361b-157">Ciągi wpisane w kroku 5 pojawiają się w przypisaniu do właściwości `Strings`.</span><span class="sxs-lookup"><span data-stu-id="e361b-157">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="e361b-158">Poniższe przykłady kodu w C# i Visual Basic pokazują kod podobny do tego, co zobaczysz, jeśli wpisano ciągi "Red", "pomarańczowy" i "żółty".</span><span class="sxs-lookup"><span data-stu-id="e361b-158">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. <span data-ttu-id="e361b-159">W **edytorze kodu**zmień wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> właściwości `Strings` na <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="e361b-159">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. <span data-ttu-id="e361b-160">Skompiluj ponownie rozwiązanie i powtórz kroki 3 i 4.</span><span class="sxs-lookup"><span data-stu-id="e361b-160">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="e361b-161">W takim przypadku **Projektant formularzy systemu Windows** emituje brak przypisania do właściwości `Strings`.</span><span class="sxs-lookup"><span data-stu-id="e361b-161">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e361b-162">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e361b-162">Next steps</span></span>

<span data-ttu-id="e361b-163">Gdy wiesz, jak serializować kolekcję typów standardowych, rozważ integrację formantów niestandardowych w środowisku czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="e361b-163">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="e361b-164">W poniższych tematach opisano sposób ulepszania integracji niestandardowych kontrolek w czasie projektowania:</span><span class="sxs-lookup"><span data-stu-id="e361b-164">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="e361b-165">[Architektura czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e361b-165">[Design-Time Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="e361b-166">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e361b-166">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="e361b-167">[Omówienie serializacji projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e361b-167">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="e361b-168">Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e361b-168">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="e361b-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e361b-169">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="e361b-170">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="e361b-170">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
