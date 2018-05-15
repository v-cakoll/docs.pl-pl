---
title: 'Porady: opracowywanie prostego formantu formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 04cedc0df60ef95acb79b651ddcbcbb34ae5e920
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="94dd6-102">Porady: opracowywanie prostego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94dd6-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="94dd6-103">W tej sekcji przedstawiono podstawowe etapy tworzenia niestandardowego formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94dd6-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="94dd6-104">Proste kontrolki opracowane w tym przewodniku umożliwia wyrównanie jego <xref:System.Windows.Forms.Control.Text%2A> właściwość zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="94dd6-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="94dd6-105">Nie podnieść lub obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="94dd6-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="94dd6-106">Aby utworzyć prosty formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="94dd6-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="94dd6-107">Definiowanie klasy, która jest pochodną <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="94dd6-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  <span data-ttu-id="94dd6-108">Definiowanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="94dd6-108">Define properties.</span></span> <span data-ttu-id="94dd6-109">(Nie należy do definiowania właściwości, ponieważ formant dziedziczy wiele właściwości z <xref:System.Windows.Forms.Control> klasy, ale większość formantów niestandardowych zazwyczaj zdefiniować dodatkowe właściwości.) Poniższy fragment kodu definiuje właściwość o nazwie `TextAlignment` który `FirstControl` jest używany do formatowania wyświetlania <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="94dd6-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="94dd6-110">Aby uzyskać więcej informacji na temat definiowania właściwości, zobacz [Przegląd właściwości](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="94dd6-110">For more information about defining properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="94dd6-111">Gdy właściwość zmiany wyświetlania kontrolki, należy wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> metodę, aby odświeżyć formantu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="94dd6-112"><xref:System.Windows.Forms.Control.Invalidate%2A> jest zdefiniowany w klasie podstawowej <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="94dd6-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="94dd6-113">Zastąpienie chronionej <xref:System.Windows.Forms.Control.OnPaint%2A> odziedziczone metody <xref:System.Windows.Forms.Control> zapewnienie logikę renderowania formantu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="94dd6-114">Jeśli nie zastępują <xref:System.Windows.Forms.Control.OnPaint%2A>, formantu nie będzie mógł się rysowanie.</span><span class="sxs-lookup"><span data-stu-id="94dd6-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="94dd6-115">W poniższy fragment kodu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda Wyświetla <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control> z wyrównanie określone przez `alignmentValue` pola.</span><span class="sxs-lookup"><span data-stu-id="94dd6-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="94dd6-116">Podaj atrybuty dla formantu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-116">Provide attributes for your control.</span></span> <span data-ttu-id="94dd6-117">Atrybuty Włącz wizualnego projektanta wyświetlić właściwości i zdarzeń formantu i jego odpowiednio w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="94dd6-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="94dd6-118">Poniższy fragment kodu stosuje atrybuty `TextAlignment` właściwości.</span><span class="sxs-lookup"><span data-stu-id="94dd6-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="94dd6-119">W projektancie, takiego jak Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atrybut (wyświetlany we fragmencie kodu) powoduje, że właściwości, które mają być wyświetlane w obszarze kategoria logiczna.</span><span class="sxs-lookup"><span data-stu-id="94dd6-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="94dd6-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atrybut powoduje opisowy ciąg mają być wyświetlane w dolnej części **właściwości** okna po `TextAlignment` właściwości jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="94dd6-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="94dd6-121">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty czasu projektowania dla składników](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="94dd6-121">For more information about attributes, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="94dd6-122">(opcjonalnie) Podaj zasobów dla formantu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="94dd6-123">Możesz podać zasobów, takich jak mapy bitowej dla formantu przy użyciu opcji kompilatora (`/res` dla C#) do pakietu zasobów za pomocą formantu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="94dd6-124">W czasie wykonywania, można pobrać zasobu przy użyciu metody <xref:System.Resources.ResourceManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="94dd6-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="94dd6-125">Aby uzyskać więcej informacji na temat tworzenia i używania zasobów, zobacz [zasobów w aplikacjach pulpitu](../../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="94dd6-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="94dd6-126">Skompiluj i wdróż formantu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-126">Compile and deploy your control.</span></span> <span data-ttu-id="94dd6-127">Aby skompilować i wdrożyć `FirstControl,` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="94dd6-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="94dd6-128">Zapisz kod w poniższym przykładzie do pliku źródłowego (na przykład FirstControl.cs lub FirstControl.vb).</span><span class="sxs-lookup"><span data-stu-id="94dd6-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="94dd6-129">Kompilowanie kodu źródłowego w zestawie i zapisz go w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94dd6-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="94dd6-130">Aby to zrobić, uruchom następujące polecenie z katalogu, który zawiera plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="94dd6-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="94dd6-131">`/t:library` — Opcja kompilatora informuje kompilator, że zestaw tworzona jest biblioteki (a nie plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="94dd6-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="94dd6-132">`/out` Opcja określa ścieżkę i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="94dd6-133">`/r` Opcja zawiera nazwę zestawy, do których odwołuje się kod.</span><span class="sxs-lookup"><span data-stu-id="94dd6-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="94dd6-134">W tym przykładzie utworzysz zestaw prywatny, który można używać tylko aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94dd6-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="94dd6-135">W związku z tym należy zapisać go w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94dd6-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="94dd6-136">Aby uzyskać więcej informacji dotyczących pakowania i wdrażania kontrolkę do dystrybucji, zobacz [wdrożenia](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="94dd6-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="94dd6-137">Poniższy przykład przedstawia kod dla `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="94dd6-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="94dd6-138">Kontroli jest ujęty w przestrzeni nazw `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="94dd6-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="94dd6-139">Przestrzeń nazw zapewnia logiczne grupowanie powiązanych typów.</span><span class="sxs-lookup"><span data-stu-id="94dd6-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="94dd6-140">Można utworzyć formantu w nowej lub istniejącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="94dd6-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="94dd6-141">W języku C# `using` deklaracji (w języku Visual Basic `Imports`) umożliwia typów można uzyskać dostęp z przestrzeni nazw, bez korzystania z w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="94dd6-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="94dd6-142">W poniższym przykładzie `using` deklaracji umożliwia kodu dostępu do tej klasy <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> tylko <xref:System.Windows.Forms.Control> zamiast w pełni kwalifikowana nazwa <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="94dd6-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="94dd6-143">Za pomocą kontrolki niestandardowej w formularzu</span><span class="sxs-lookup"><span data-stu-id="94dd6-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="94dd6-144">W poniższym przykładzie przedstawiono prosty formularz, który używa `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="94dd6-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="94dd6-145">Tworzy trzy wystąpienia `FirstControl`, każdy z inną wartością `TextAlignment` właściwości.</span><span class="sxs-lookup"><span data-stu-id="94dd6-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="94dd6-146">Aby skompilować i uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="94dd6-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="94dd6-147">Zapisz kod w poniższym przykładzie do pliku źródłowego (SimpleForm.cs lub SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="94dd6-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="94dd6-148">Kompilowanie kodu źródłowego do pliku wykonywalnego zestawu, wykonując następujące polecenie z katalogu, który zawiera plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="94dd6-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="94dd6-149">Zestaw zawierający klasę jest CustomWinControls.dll `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="94dd6-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="94dd6-150">Ten zestaw musi być w tym samym katalogu co plik źródłowy dla formularza, który uzyskuje dostęp do niego (SimpleForm.cs lub SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="94dd6-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="94dd6-151">Wykonanie SimpleForm.exe przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="94dd6-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="94dd6-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94dd6-152">See Also</span></span>  
 [<span data-ttu-id="94dd6-153">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94dd6-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="94dd6-154">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94dd6-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
