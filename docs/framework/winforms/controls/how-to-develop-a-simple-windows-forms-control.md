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
ms.openlocfilehash: 07a4de944e36b0be1a6196d08df33c4f3ab24bcc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387041"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="02d9f-102">Porady: opracowywanie prostego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="02d9f-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="02d9f-103">W tej sekcji przedstawiono podstawowe etapy tworzenia niestandardowego formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="02d9f-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="02d9f-104">Prosty formant opracowanych w tym przewodniku umożliwia wyrównanie jego <xref:System.Windows.Forms.Control.Text%2A> właściwości, które mają być zmienione.</span><span class="sxs-lookup"><span data-stu-id="02d9f-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="02d9f-105">Nie podnieść lub obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="02d9f-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="02d9f-106">Aby utworzyć prosty formant niestandardowy</span><span class="sxs-lookup"><span data-stu-id="02d9f-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="02d9f-107">Definiowanie klasy, która jest pochodną <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02d9f-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2.  <span data-ttu-id="02d9f-108">Zdefiniuj właściwości.</span><span class="sxs-lookup"><span data-stu-id="02d9f-108">Define properties.</span></span> <span data-ttu-id="02d9f-109">(Nie wymagane do zdefiniowania właściwości, ponieważ formant dziedziczy wiele właściwości z <xref:System.Windows.Forms.Control> klasy, ale większość niestandardowe formanty ogólnie zdefiniować dodatkowe właściwości.) Poniższy fragment kodu definiuje właściwość o nazwie `TextAlignment` , `FirstControl` jest używany do formatowania wyświetlania <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="02d9f-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="02d9f-110">Aby uzyskać więcej informacji na temat definiowania właściwości, zobacz [Przegląd właściwości](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="02d9f-110">For more information about defining properties, see [Properties Overview](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="02d9f-111">Po ustawieniu właściwości, która zmienia wyświetlania kontrolki, należy wywołać <xref:System.Windows.Forms.Control.Invalidate%2A> metodę, aby odświeżyć formantu.</span><span class="sxs-lookup"><span data-stu-id="02d9f-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="02d9f-112"><xref:System.Windows.Forms.Control.Invalidate%2A> jest zdefiniowany w klasie bazowej <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="02d9f-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="02d9f-113">Zastąp chronionego <xref:System.Windows.Forms.Control.OnPaint%2A> metody dziedziczone z <xref:System.Windows.Forms.Control> zapewnienie logikę renderowania formantu.</span><span class="sxs-lookup"><span data-stu-id="02d9f-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="02d9f-114">Jeśli nie zastąpisz <xref:System.Windows.Forms.Control.OnPaint%2A>, formant nie będzie można narysować sam.</span><span class="sxs-lookup"><span data-stu-id="02d9f-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="02d9f-115">W poniższy fragment kodu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda Wyświetla <xref:System.Windows.Forms.Control.Text%2A> właściwość dziedziczona z <xref:System.Windows.Forms.Control> z wyrównaniem, określony przez `alignmentValue` pola.</span><span class="sxs-lookup"><span data-stu-id="02d9f-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="02d9f-116">Podaj atrybuty kontrolki.</span><span class="sxs-lookup"><span data-stu-id="02d9f-116">Provide attributes for your control.</span></span> <span data-ttu-id="02d9f-117">Atrybuty Włącz projektanta wizualnego wyświetlić kontrolki i ich właściwości i zdarzenia odpowiednio w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="02d9f-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="02d9f-118">Poniższy fragment kodu, ma zastosowanie atrybutów, które mają `TextAlignment` właściwości.</span><span class="sxs-lookup"><span data-stu-id="02d9f-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="02d9f-119">W projektancie, takich jak Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atrybutu (pokazano we fragmencie kodu) powoduje, że właściwości, które mają być wyświetlane w obszarze kategoria logiczna.</span><span class="sxs-lookup"><span data-stu-id="02d9f-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="02d9f-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atrybutu powoduje, że opisowy ciąg, który będzie wyświetlany w dolnej części **właściwości** okna po `TextAlignment` właściwości jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="02d9f-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="02d9f-121">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty czasu projektowania dla składników](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="02d9f-121">For more information about attributes, see [Design-Time Attributes for Components](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="02d9f-122">(opcjonalnie) Zawierają zasoby dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="02d9f-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="02d9f-123">Możesz podać zasobu, takie jak mapy bitowej kontrolki przy użyciu opcji kompilatora (`/res` dla języka C#) do zasobów pakietu przy użyciu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="02d9f-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="02d9f-124">W czasie wykonywania, można pobrać zasobu za pomocą metody <xref:System.Resources.ResourceManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="02d9f-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="02d9f-125">Aby uzyskać więcej informacji na temat tworzenia i używania zasobów, zobacz [zasoby w aplikacjach pulpitu](../../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="02d9f-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="02d9f-126">Skompiluj i wdróż formantu.</span><span class="sxs-lookup"><span data-stu-id="02d9f-126">Compile and deploy your control.</span></span> <span data-ttu-id="02d9f-127">Aby skompilować i wdrożyć `FirstControl,` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="02d9f-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="02d9f-128">Zapisz kod w następującym przykładzie do pliku źródłowego (na przykład FirstControl.cs lub FirstControl.vb).</span><span class="sxs-lookup"><span data-stu-id="02d9f-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="02d9f-129">Skompilować kod źródłowy do zestawu i zapisz go w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02d9f-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="02d9f-130">W tym celu wykonaj następujące polecenie z katalogu, który zawiera plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="02d9f-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="02d9f-131">`/t:library` — Opcja kompilatora informuje kompilator, to zestaw tworzysz bibliotekę (i nie plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="02d9f-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="02d9f-132">`/out` Opcja określa ścieżkę i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="02d9f-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="02d9f-133">`/r` Opcja zawiera nazwę zestawów, które są przywoływane przez kod.</span><span class="sxs-lookup"><span data-stu-id="02d9f-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="02d9f-134">W tym przykładzie utworzysz zestaw prywatny, można użyć tylko w Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02d9f-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="02d9f-135">W związku z tym należy zapisać go w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="02d9f-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="02d9f-136">Aby uzyskać więcej informacji na temat pakowania i wdrażania kontrolkę do dystrybucji, zobacz [wdrożenia](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="02d9f-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="02d9f-137">Poniższy przykład przedstawia kod dla `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="02d9f-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="02d9f-138">Kontrolka jest ujęty w przestrzeni nazw `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="02d9f-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="02d9f-139">Przestrzeń nazw zapewnia powodują ustawienie logicznego grupowania powiązanych typów.</span><span class="sxs-lookup"><span data-stu-id="02d9f-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="02d9f-140">Można utworzyć kontrolki w nowej lub istniejącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="02d9f-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="02d9f-141">W języku C# `using` deklaracji (w języku Visual Basic `Imports`) zezwala na typy, które były dostępne z przestrzeni nazw bez korzystania z w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="02d9f-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="02d9f-142">W poniższym przykładzie `using` deklaracja umożliwia kodu dostępu do tej klasy <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> tylko <xref:System.Windows.Forms.Control> zamiast konieczności używania w pełni kwalifikowana nazwa <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02d9f-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="02d9f-143">Za pomocą niestandardowej kontrolki na formularzu</span><span class="sxs-lookup"><span data-stu-id="02d9f-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="02d9f-144">W poniższym przykładzie przedstawiono prosty formularz, który używa `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="02d9f-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="02d9f-145">Tworzy trzy wystąpienia `FirstControl`, każdy z inną wartością `TextAlignment` właściwości.</span><span class="sxs-lookup"><span data-stu-id="02d9f-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="02d9f-146">Aby skompilować i uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="02d9f-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="02d9f-147">Zapisz kod w przykładzie poniżej do pliku źródłowego (SimpleForm.cs lub SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="02d9f-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="02d9f-148">Skompilować kod źródłowy do zestawu pliku wykonywalnego, wykonując następujące polecenie z katalogu, który zawiera plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="02d9f-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="02d9f-149">CustomWinControls.dll jest zestawem, który zawiera klasę `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="02d9f-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="02d9f-150">Ten zestaw musi być w tym samym katalogu co plik źródłowy do formularza, który uzyskuje dostęp do niego (SimpleForm.cs lub SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="02d9f-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="02d9f-151">Wykonaj SimpleForm.exe przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="02d9f-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="02d9f-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02d9f-152">See Also</span></span>  
 [<span data-ttu-id="02d9f-153">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02d9f-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="02d9f-154">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02d9f-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
