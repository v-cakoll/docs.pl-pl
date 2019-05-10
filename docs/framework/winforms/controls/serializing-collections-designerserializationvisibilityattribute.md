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
ms.openlocfilehash: c8321f98b25026e32e7c69f7029f2c589d0567f7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211599"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="22946-102">Przewodnik: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="22946-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>

<span data-ttu-id="22946-103">Kontrolki niestandardowe czasami udostępni kolekcji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="22946-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="22946-104">W tym instruktażu przedstawiono sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> klasy do kontrolowania, jak kolekcja jest serializowany w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="22946-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="22946-105">Stosowanie <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> wartości właściwości z kolekcji zapewnia właściwość będzie serializowana.</span><span class="sxs-lookup"><span data-stu-id="22946-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="22946-106">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="22946-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22946-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="22946-107">Prerequisites</span></span>

<span data-ttu-id="22946-108">Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="22946-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="22946-109">Tworzenie formantu za pomocą kolekcji serializacji</span><span class="sxs-lookup"><span data-stu-id="22946-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="22946-110">Pierwszym krokiem jest, aby utworzyć formant, który jest możliwy do serializacji kolekcji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="22946-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="22946-111">Możesz edytować zawartość tej kolekcji przy użyciu **— Edytor kolekcji**, który jest dostępny z **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="22946-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="22946-112">W programie Visual Studio Utwórz projekt Biblioteka formantów Windows o nazwie `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="22946-112">In Visual Studio, create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="22946-113">Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="22946-113">For more information, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="22946-114">Zmień nazwę `UserControl1` do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-114">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="22946-115">Aby uzyskać więcej informacji, zobacz [symbolu kodu Refaktoryzacja zmiany nazwy](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="22946-115">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="22946-116">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> właściwość `10`.</span><span class="sxs-lookup"><span data-stu-id="22946-116">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>

4. <span data-ttu-id="22946-117">Miejsce <xref:System.Windows.Forms.TextBox> w kontrolce `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-117">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="22946-118">Wybierz <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="22946-118">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="22946-119">W **właściwości** okna, ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="22946-119">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="22946-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="22946-120">Property</span></span>|<span data-ttu-id="22946-121">Zmień na</span><span class="sxs-lookup"><span data-stu-id="22946-121">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="22946-122">**Wielowierszowy**</span><span class="sxs-lookup"><span data-stu-id="22946-122">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="22946-123">**Dock**</span><span class="sxs-lookup"><span data-stu-id="22946-123">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="22946-124">**Paski przewijania**</span><span class="sxs-lookup"><span data-stu-id="22946-124">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="22946-125">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="22946-125">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="22946-126">W **Edytor kodu**, Zadeklaruj pola tablicy ciągów o nazwie `stringsValue` w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-126">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="22946-127">Zdefiniuj `Strings` właściwość `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-127">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="22946-128"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Wartość jest używana do włączenia serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="22946-128">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="22946-129">Naciśnij klawisz **F5** skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="22946-129">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="22946-130">Znajdź `Strings` właściwość <xref:System.Windows.Forms.PropertyGrid> z **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="22946-130">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="22946-131">Kliknij przycisk `Strings` właściwości, następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="22946-131">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="22946-132">Wprowadź kilka ciągów w **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="22946-132">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="22946-133">Oddziel je, naciskając klawisz **Enter** klucza na końcu każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="22946-133">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="22946-134">Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="22946-134">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="22946-135">Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-135">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serializing-a-collection-property"></a><span data-ttu-id="22946-136">Serializowanie właściwości kolekcji</span><span class="sxs-lookup"><span data-stu-id="22946-136">Serializing a Collection Property</span></span>

<span data-ttu-id="22946-137">Aby sprawdzić zachowanie serializacji kontrolki, będzie umieścić go w formularzu i zmieniać zawartość kolekcji przy użyciu **— Edytor kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="22946-137">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="22946-138">Można wyświetlić stan kolekcji serializacji, analizując specjalny plik projektanta, do którego **Windows Forms Designer** emituje kod.</span><span class="sxs-lookup"><span data-stu-id="22946-138">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

### <a name="to-serialize-a-collection"></a><span data-ttu-id="22946-139">Do serializacji kolekcji</span><span class="sxs-lookup"><span data-stu-id="22946-139">To serialize a collection</span></span>

1. <span data-ttu-id="22946-140">Dodaj projekt aplikacji Windows do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="22946-140">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="22946-141">Nadaj projektowi nazwę `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="22946-141">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="22946-142">W **przybornika**, Znajdź kartę o nazwie **składniki SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="22946-142">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="22946-143">Na tej karcie można znaleźć `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-143">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="22946-144">Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="22946-144">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="22946-145">Miejsce `SerializationDemoControl` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="22946-145">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="22946-146">Znajdź `Strings` właściwość **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="22946-146">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="22946-147">Kliknij przycisk `Strings` właściwości, następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="22946-147">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="22946-148">Wpisz kilka ciągów w **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="22946-148">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="22946-149">Oddziel je, naciskając klawisz ENTER na końcu każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="22946-149">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="22946-150">Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="22946-150">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="22946-151">Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="22946-151">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

1. <span data-ttu-id="22946-152">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="22946-152">In **Solution Explorer**, click the **Show All Files** button.</span></span>

2. <span data-ttu-id="22946-153">Otwórz **Form1** węzła.</span><span class="sxs-lookup"><span data-stu-id="22946-153">Open the **Form1** node.</span></span> <span data-ttu-id="22946-154">Podrzędne jest plik o nazwie **Form1.Designer.cs** lub **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="22946-154">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="22946-155">Jest to plik, do którego **Windows Forms Designer** emituje kod reprezentujący stan projektowania formularza i jego formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="22946-155">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="22946-156">Otwórz ten plik w **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="22946-156">Open this file in the **Code Editor**.</span></span>

3. <span data-ttu-id="22946-157">Otwórz region o nazwie **kod wygenerowany przez projektanta formularzy Windows** i Znajdź sekcję etykietą **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="22946-157">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="22946-158">Pod tą etykietą jest kod reprezentujący Zserializowany stan kontrolki.</span><span class="sxs-lookup"><span data-stu-id="22946-158">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="22946-159">Ciągi wpisywane w kroku 5 są wyświetlane w przypisaniu do `Strings` właściwości.</span><span class="sxs-lookup"><span data-stu-id="22946-159">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="22946-160">W poniższych przykładach kodu w języku C# i Visual Basic, Pokaż kod podobny do będzie wyświetlanych Jeśli wpisano ciągi "red", "pomarańczowy" i "żółty".</span><span class="sxs-lookup"><span data-stu-id="22946-160">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

4. <span data-ttu-id="22946-161">W **Edytor kodu**, zmień wartość właściwości <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` właściwość <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="22946-161">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

5. <span data-ttu-id="22946-162">Ponownie skompiluj rozwiązanie i powtórz kroki 3 i 4.</span><span class="sxs-lookup"><span data-stu-id="22946-162">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="22946-163">W tym przypadku **Windows Forms Designer** emituje żadnego przypisania `Strings` właściwości.</span><span class="sxs-lookup"><span data-stu-id="22946-163">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="22946-164">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="22946-164">Next Steps</span></span>

<span data-ttu-id="22946-165">Wiesz, jak do serializacji kolekcji standardowych typów, należy wziąć pod uwagę integrowanie Kontrolki niestandardowe głębiej środowisku czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="22946-165">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="22946-166">W poniższych tematach opisano, jak poprawić integracji czasu projektowania dla kontrolek niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="22946-166">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="22946-167">[Architektura czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="22946-167">[Design-Time Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="22946-168">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22946-168">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="22946-169">[Przegląd serializacji projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="22946-169">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="22946-170">Przewodnik: Tworzenie kontrolki formularzy Windows wykorzystującego funkcje czasu projektowania w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="22946-170">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="22946-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22946-171">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- <span data-ttu-id="22946-172">[Przegląd serializacji projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="22946-172">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>
- <span data-ttu-id="22946-173">[Instrukcje: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="22946-173">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
- [<span data-ttu-id="22946-174">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="22946-174">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
