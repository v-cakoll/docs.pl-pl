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
ms.openlocfilehash: a502ecc30911f2296bf48eaa195f5b6452b7588a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541301"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="ceddb-102">Porady: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="ceddb-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="ceddb-103">Kontrolki niestandardowe czasami powoduje to udostępnienie kolekcji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="ceddb-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="ceddb-104">W tym przewodniku przedstawiono sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> klasę, aby kontrolować sposób kolekcji jest serializowany w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="ceddb-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="ceddb-105">Stosowanie <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> zapewnia wartość właściwości z kolekcji zostaną Zserializowane właściwości.</span><span class="sxs-lookup"><span data-stu-id="ceddb-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="ceddb-106">Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: serializacji kolekcji o standardowych typów za pomocą DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span><span class="sxs-lookup"><span data-stu-id="ceddb-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceddb-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="ceddb-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ceddb-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="ceddb-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ceddb-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ceddb-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ceddb-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ceddb-110">Prerequisites</span></span>  
 <span data-ttu-id="ceddb-111">W celu przeprowadzenia tego instruktażu potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="ceddb-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="ceddb-112">Wystarczających uprawnień, aby mieć możliwość tworzenia i uruchamiania projektów aplikacji formularzy systemu Windows na komputerze, którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ceddb-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="ceddb-113">Tworzenie formantu, który ma serializacji kolekcji</span><span class="sxs-lookup"><span data-stu-id="ceddb-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="ceddb-114">Pierwszym krokiem jest można utworzyć formantu, który ma serializacji kolekcji jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="ceddb-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="ceddb-115">Można edytować zawartość tej kolekcji przy użyciu **edytora kolekcji**, które jest dostępne **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="ceddb-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="ceddb-116">Aby utworzyć formant z kolekcji serializacji</span><span class="sxs-lookup"><span data-stu-id="ceddb-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="ceddb-117">Tworzenie projektu Biblioteka formantów systemu Windows o nazwie `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="ceddb-118">Aby uzyskać więcej informacji, zobacz [szablon biblioteki systemu Windows formantu](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="ceddb-118">For more information, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="ceddb-119">Zmień nazwę `UserControl1` do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="ceddb-120">Aby uzyskać więcej informacji, zobacz [porady: Zmienianie nazwy identyfikatorów](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span><span class="sxs-lookup"><span data-stu-id="ceddb-120">For more information, see [How to: Rename Identifiers](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span></span>  
  
3.  <span data-ttu-id="ceddb-121">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> właściwości `10`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="ceddb-122">Miejsce <xref:System.Windows.Forms.TextBox> kontroli w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="ceddb-123">Wybierz <xref:System.Windows.Forms.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="ceddb-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="ceddb-124">W **właściwości** okna, ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="ceddb-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="ceddb-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ceddb-125">Property</span></span>|<span data-ttu-id="ceddb-126">Zmień na</span><span class="sxs-lookup"><span data-stu-id="ceddb-126">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="ceddb-127">**Wiele linii**</span><span class="sxs-lookup"><span data-stu-id="ceddb-127">**Multiline**</span></span>|`true`|  
    |<span data-ttu-id="ceddb-128">**Doku.**</span><span class="sxs-lookup"><span data-stu-id="ceddb-128">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |<span data-ttu-id="ceddb-129">**Paski przewijania**</span><span class="sxs-lookup"><span data-stu-id="ceddb-129">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |<span data-ttu-id="ceddb-130">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="ceddb-130">**ReadOnly**</span></span>|`true`|  
  
6.  <span data-ttu-id="ceddb-131">W **edytora kodu**, Zadeklaruj pola tablicy ciągu o nazwie `stringsValue` w `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="ceddb-132">Zdefiniuj `Strings` właściwość `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceddb-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Wartość jest używana do włączenia serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ceddb-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="ceddb-134">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="ceddb-135">Znajdź `Strings` właściwości w <xref:System.Windows.Forms.PropertyGrid> z **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="ceddb-136">Kliknij przycisk `Strings` właściwości, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **edytora kolekcji ciąg**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="ceddb-137">Wprowadź kilka ciągów w **edytora kolekcji ciąg**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="ceddb-138">Oddziel je po naciśnięciu klawisza ENTER na końcu każdej ciągu.</span><span class="sxs-lookup"><span data-stu-id="ceddb-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="ceddb-139">Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="ceddb-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceddb-140">Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="ceddb-141">Właściwości kolekcji serializacji</span><span class="sxs-lookup"><span data-stu-id="ceddb-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="ceddb-142">Aby przetestować działanie serializacji formantu, będzie umieszczenie go w formie i zmienić zawartość kolekcji z **edytora kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="ceddb-143">Analizując projektanta specjalny plik, w którym można zobaczyć stan serializacji kolekcji **Projektant formularzy systemu Windows** emituje kod.</span><span class="sxs-lookup"><span data-stu-id="ceddb-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="ceddb-144">Do serializacji kolekcji</span><span class="sxs-lookup"><span data-stu-id="ceddb-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="ceddb-145">Dodaj projekt aplikacji systemu Windows do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ceddb-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="ceddb-146">Nazwij projekt `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="ceddb-147">W **przybornika**, Znajdź kartę o nazwie **składniki SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="ceddb-148">Na tej karcie można znaleźć `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="ceddb-149">Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="ceddb-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="ceddb-150">Miejsce `SerializationDemoControl` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ceddb-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="ceddb-151">Znajdź `Strings` właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="ceddb-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="ceddb-152">Kliknij przycisk `Strings` właściwości, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **edytora kolekcji ciąg**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="ceddb-153">Wpisz kilka ciągów w **edytora kolekcji ciąg**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="ceddb-154">Oddziel je po naciśnięciu klawisza ENTER na końcu każdej ciągu.</span><span class="sxs-lookup"><span data-stu-id="ceddb-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="ceddb-155">Kliknij przycisk **OK** po zakończeniu wprowadzania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="ceddb-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceddb-156">Ciągi wpisany są wyświetlane w <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="ceddb-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="ceddb-157">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ceddb-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="ceddb-158">Otwórz **Form1** węzła.</span><span class="sxs-lookup"><span data-stu-id="ceddb-158">Open the **Form1** node.</span></span> <span data-ttu-id="ceddb-159">Podrzędne jest plik o nazwie **Form1.Designer.cs** lub **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="ceddb-160">Jest to plik, do którego **Projektant formularzy systemu Windows** emituje kod reprezentujący stan czasu projektowania formularza i jej kontrolkach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ceddb-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="ceddb-161">Otwórz ten plik w **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="ceddb-162">Otwórz obszar o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows** i Znajdź sekcję etykietą **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="ceddb-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="ceddb-163">Pod tą etykietą jest kod reprezentujący Zserializowany stan formantu.</span><span class="sxs-lookup"><span data-stu-id="ceddb-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="ceddb-164">Ciągi wpisane w kroku 5 są wyświetlane w przypisaniu do `Strings` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ceddb-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="ceddb-165">W poniższych przykładach kodu w języku C# i Visual Basic, Pokaż kodu podobne do co zobaczysz Jeśli wpisano ciągów "red", "pomarańczowy" i "żółty".</span><span class="sxs-lookup"><span data-stu-id="ceddb-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="ceddb-166">W **edytora kodu**, zmień wartość <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` właściwości <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="ceddb-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="ceddb-167">Ponowne kompilowanie rozwiązania i powtórz kroki 3 i 4.</span><span class="sxs-lookup"><span data-stu-id="ceddb-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceddb-168">W takim przypadku **Projektant formularzy systemu Windows** emituje żadnego przypisania `Strings` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ceddb-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ceddb-169">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ceddb-169">Next Steps</span></span>  
 <span data-ttu-id="ceddb-170">Po sprawdzeniu, jak do serializacji kolekcji standardowych typów, należy wziąć pod uwagę integrowanie Kontrolki niestandardowe głębsze środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="ceddb-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="ceddb-171">W poniższych tematach opisano, jak zwiększyć integracji czasu projektowania Kontrolki niestandardowe:</span><span class="sxs-lookup"><span data-stu-id="ceddb-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="ceddb-172">Architektura w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="ceddb-172">Design-Time Architecture</span></span>](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [<span data-ttu-id="ceddb-173">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ceddb-173">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="ceddb-174">Omówienie projektanta serializacji</span><span class="sxs-lookup"><span data-stu-id="ceddb-174">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [<span data-ttu-id="ceddb-175">Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ceddb-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="ceddb-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ceddb-176">See Also</span></span>  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [<span data-ttu-id="ceddb-177">Omówienie projektanta serializacji</span><span class="sxs-lookup"><span data-stu-id="ceddb-177">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [<span data-ttu-id="ceddb-178">Porady: serializacji kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="ceddb-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [<span data-ttu-id="ceddb-179">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="ceddb-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
