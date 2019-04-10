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
ms.openlocfilehash: 791b2ea1497b8b884d066894e925785fd1bb6f7d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305211"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="c8e37-102">Przewodnik: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="c8e37-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="c8e37-103">Kontrolki niestandardowe czasami udostępni kolekcji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="c8e37-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="c8e37-104">W tym instruktażu przedstawiono sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> klasy do kontrolowania, jak kolekcja jest serializowany w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="c8e37-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="c8e37-105">Stosowanie <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> wartości właściwości z kolekcji zapewnia właściwość będzie serializowana.</span><span class="sxs-lookup"><span data-stu-id="c8e37-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="c8e37-106">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="c8e37-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e37-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c8e37-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c8e37-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c8e37-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c8e37-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c8e37-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c8e37-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c8e37-110">Prerequisites</span></span>  
 <span data-ttu-id="c8e37-111">Aby ukończyć ten przewodnik, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="c8e37-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="c8e37-112">Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8e37-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="c8e37-113">Tworzenie formantu, który ma możliwy do serializacji kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8e37-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="c8e37-114">Pierwszym krokiem jest, aby utworzyć formant, który jest możliwy do serializacji kolekcji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="c8e37-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="c8e37-115">Możesz edytować zawartość tej kolekcji przy użyciu **— Edytor kolekcji**, który jest dostępny z **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="c8e37-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="c8e37-116">Aby utworzyć kontrolkę za pomocą kolekcji serializacji</span><span class="sxs-lookup"><span data-stu-id="c8e37-116">To create a control with a serializable collection</span></span>  
  
1. <span data-ttu-id="c8e37-117">Utwórz projekt Biblioteka formantów Windows o nazwie `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="c8e37-118">Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c8e37-118">For more information, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="c8e37-119">Zmień nazwę `UserControl1` do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="c8e37-120">Aby uzyskać więcej informacji, zobacz [symbolu kodu Refaktoryzacja zmiany nazwy](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="c8e37-120">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>  
  
3. <span data-ttu-id="c8e37-121">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> właściwość `10`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4. <span data-ttu-id="c8e37-122">Miejsce <xref:System.Windows.Forms.TextBox> w kontrolce `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5. <span data-ttu-id="c8e37-123">Wybierz <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c8e37-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="c8e37-124">W **właściwości** okna, ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="c8e37-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="c8e37-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c8e37-125">Property</span></span>|<span data-ttu-id="c8e37-126">Zmień na</span><span class="sxs-lookup"><span data-stu-id="c8e37-126">Change to</span></span>|  
    |--------------|---------------|  
    |**<span data-ttu-id="c8e37-127">Wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="c8e37-127">Multiline</span></span>**|`true`|  
    |**<span data-ttu-id="c8e37-128">Dock</span><span class="sxs-lookup"><span data-stu-id="c8e37-128">Dock</span></span>**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**<span data-ttu-id="c8e37-129">Paski przewijania</span><span class="sxs-lookup"><span data-stu-id="c8e37-129">ScrollBars</span></span>**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**<span data-ttu-id="c8e37-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c8e37-130">ReadOnly</span></span>**|`true`|  
  
6. <span data-ttu-id="c8e37-131">W **Edytor kodu**, Zadeklaruj pola tablicy ciągów o nazwie `stringsValue` w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7. <span data-ttu-id="c8e37-132">Zdefiniuj `Strings` właściwość `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e37-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Wartość jest używana do włączenia serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8e37-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1. <span data-ttu-id="c8e37-134">Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2. <span data-ttu-id="c8e37-135">Znajdź `Strings` właściwość <xref:System.Windows.Forms.PropertyGrid> z **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="c8e37-136">Kliknij przycisk `Strings` właściwości, następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3. <span data-ttu-id="c8e37-137">Wprowadź kilka ciągów w **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="c8e37-138">Oddziel je, naciskając klawisz ENTER na końcu każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="c8e37-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="c8e37-139">Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="c8e37-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e37-140">Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="c8e37-141">Serializowanie właściwości kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8e37-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="c8e37-142">Aby sprawdzić zachowanie serializacji kontrolki, będzie umieścić go w formularzu i zmieniać zawartość kolekcji przy użyciu **— Edytor kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="c8e37-143">Można wyświetlić stan kolekcji serializacji, patrząc na plik projektanta specjalny, do którego **Windows Forms Designer** emituje kod.</span><span class="sxs-lookup"><span data-stu-id="c8e37-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="c8e37-144">Do serializacji kolekcji</span><span class="sxs-lookup"><span data-stu-id="c8e37-144">To serialize a collection</span></span>  
  
1. <span data-ttu-id="c8e37-145">Dodaj projekt aplikacji Windows do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c8e37-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="c8e37-146">Nadaj projektowi nazwę `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2. <span data-ttu-id="c8e37-147">W **przybornika**, Znajdź kartę o nazwie **składniki SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="c8e37-148">Na tej karcie można znaleźć `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="c8e37-149">Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="c8e37-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3. <span data-ttu-id="c8e37-150">Miejsce `SerializationDemoControl` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="c8e37-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4. <span data-ttu-id="c8e37-151">Znajdź `Strings` właściwość **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="c8e37-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="c8e37-152">Kliknij przycisk `Strings` właściwości, następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5. <span data-ttu-id="c8e37-153">Wpisz kilka ciągów w **Edytor kolekcji ciągów**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="c8e37-154">Oddziel je, naciskając klawisz ENTER na końcu każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="c8e37-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="c8e37-155">Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="c8e37-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e37-156">Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c8e37-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1. <span data-ttu-id="c8e37-157">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c8e37-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2. <span data-ttu-id="c8e37-158">Otwórz **Form1** węzła.</span><span class="sxs-lookup"><span data-stu-id="c8e37-158">Open the **Form1** node.</span></span> <span data-ttu-id="c8e37-159">Podrzędne jest plik o nazwie **Form1.Designer.cs** lub **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="c8e37-160">Jest to plik, do którego **Windows Forms Designer** emituje kod reprezentujący stan projektowania formularza i jego formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c8e37-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="c8e37-161">Otwórz ten plik w **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-161">Open this file in the **Code Editor**.</span></span>  
  
3. <span data-ttu-id="c8e37-162">Otwórz region o nazwie **kod wygenerowany przez projektanta formularzy Windows** i Znajdź sekcję etykietą **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="c8e37-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="c8e37-163">Pod tą etykietą jest kod reprezentujący Zserializowany stan kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c8e37-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="c8e37-164">Ciągi wpisywane w kroku 5 są wyświetlane w przypisaniu do `Strings` właściwości.</span><span class="sxs-lookup"><span data-stu-id="c8e37-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="c8e37-165">W poniższych przykładach kodu w języku C# i Visual Basic, Pokaż kod podobny do będzie wyświetlanych Jeśli wpisano ciągi "red", "pomarańczowy" i "żółty".</span><span class="sxs-lookup"><span data-stu-id="c8e37-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4. <span data-ttu-id="c8e37-166">W **Edytor kodu**, zmień wartość właściwości <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` właściwość <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="c8e37-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="c8e37-167">Ponownie skompiluj rozwiązanie i powtórz kroki 3 i 4.</span><span class="sxs-lookup"><span data-stu-id="c8e37-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e37-168">W tym przypadku **Windows Forms Designer** emituje żadnego przypisania `Strings` właściwości.</span><span class="sxs-lookup"><span data-stu-id="c8e37-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c8e37-169">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c8e37-169">Next Steps</span></span>  
 <span data-ttu-id="c8e37-170">Wiesz, jak do serializacji kolekcji standardowych typów, należy wziąć pod uwagę integrowanie Kontrolki niestandardowe głębiej środowisku czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="c8e37-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="c8e37-171">W poniższych tematach opisano, jak poprawić integracji czasu projektowania dla kontrolek niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="c8e37-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="c8e37-172">Architektura czasu projektowania</span><span class="sxs-lookup"><span data-stu-id="c8e37-172">Design-Time Architecture</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))  
  
-   [<span data-ttu-id="c8e37-173">Atrybuty w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c8e37-173">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="c8e37-174">Przegląd serializacji projektanta</span><span class="sxs-lookup"><span data-stu-id="c8e37-174">Designer Serialization Overview</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))  
  
-   [<span data-ttu-id="c8e37-175">Przewodnik: tworzenie kontrolki formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8e37-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="c8e37-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8e37-176">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="c8e37-177">Przegląd serializacji projektanta</span><span class="sxs-lookup"><span data-stu-id="c8e37-177">Designer Serialization Overview</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))
- [<span data-ttu-id="c8e37-178">Instrukcje: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="c8e37-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
- [<span data-ttu-id="c8e37-179">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="c8e37-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
