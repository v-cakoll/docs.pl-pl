---
title: Opracowywanie prostej kontrolki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 5383cee5358dbd260fc6c023d3db607da6b10ea4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742255"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="4b4f6-102">Porady: opracowywanie prostego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4b4f6-102">How to: Develop a Simple Windows Forms Control</span></span>

<span data-ttu-id="4b4f6-103">Ta sekcja przeprowadzi Cię przez kluczowe kroki tworzenia niestandardowej kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="4b4f6-104">Prosta kontrolka opracowana w tym instruktażu umożliwia zmianę wyrównania właściwości <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="4b4f6-105">Nie zgłasza ani nie obsługuje zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-105">It does not raise or handle events.</span></span>

### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="4b4f6-106">Aby utworzyć prostą kontrolkę niestandardową</span><span class="sxs-lookup"><span data-stu-id="4b4f6-106">To create a simple custom control</span></span>

1. <span data-ttu-id="4b4f6-107">Zdefiniuj klasę, która pochodzi od <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. <span data-ttu-id="4b4f6-108">Zdefiniuj właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-108">Define properties.</span></span> <span data-ttu-id="4b4f6-109">(Nie trzeba definiować właściwości, ponieważ kontrolka dziedziczy wiele właściwości z klasy <xref:System.Windows.Forms.Control>, ale większość formantów niestandardowych zwykle definiuje dodatkowe właściwości.) Poniższy fragment kodu definiuje właściwość o nazwie `TextAlignment`, która `FirstControl` używa do formatowania wyświetlania właściwości <xref:System.Windows.Forms.Control.Text%2A> dziedziczonej z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="4b4f6-110">Aby uzyskać więcej informacji na temat definiowania właściwości, zobacz [Omówienie właściwości](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-110">For more information about defining properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     <span data-ttu-id="4b4f6-111">Po ustawieniu właściwości, która zmienia wizualizację wyświetlania kontrolki, należy wywołać metodę <xref:System.Windows.Forms.Control.Invalidate%2A>, aby ponownie narysować formant.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="4b4f6-112"><xref:System.Windows.Forms.Control.Invalidate%2A> jest zdefiniowany w klasie bazowej <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>

3. <span data-ttu-id="4b4f6-113">Przesłoń metodę chronioną <xref:System.Windows.Forms.Control.OnPaint%2A> dziedziczoną z <xref:System.Windows.Forms.Control>, aby zapewnić logikę renderowania dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="4b4f6-114">Jeśli nie zastąpisz <xref:System.Windows.Forms.Control.OnPaint%2A>, formant nie będzie mógł narysować siebie.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="4b4f6-115">W poniższym fragmencie kodu Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> wyświetla Właściwość <xref:System.Windows.Forms.Control.Text%2A> dziedziczoną z <xref:System.Windows.Forms.Control> z wyrównaniem określonym przez pole `alignmentValue`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. <span data-ttu-id="4b4f6-116">Podaj atrybuty dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-116">Provide attributes for your control.</span></span> <span data-ttu-id="4b4f6-117">Atrybuty umożliwiają projektantowi wizualnemu wyświetlanie kontrolki i jej właściwości i zdarzeń odpowiednio w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="4b4f6-118">Poniższy fragment kodu stosuje atrybuty do właściwości `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="4b4f6-119">W projektancie, takim jak Visual Studio, atrybut <xref:System.ComponentModel.CategoryAttribute.Category%2A> (pokazany w fragmencie kodu) powoduje, że właściwość jest wyświetlana w kategorii logicznej.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="4b4f6-120">Atrybut <xref:System.ComponentModel.DescriptionAttribute.Description%2A> powoduje wyświetlenie ciągu opisowego w dolnej części okna **Właściwości** po wybraniu właściwości `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="4b4f6-121">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-121">For more information about attributes, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. <span data-ttu-id="4b4f6-122">obowiązkowe Zapewnianie zasobów dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="4b4f6-123">Możesz dostarczyć zasób, taki jak mapa bitowa, dla kontrolki przy użyciu opcji kompilatora (`/res` for C#), aby spakować zasoby z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="4b4f6-124">W czasie wykonywania zasób można pobrać przy użyciu metod klasy <xref:System.Resources.ResourceManager>.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="4b4f6-125">Aby uzyskać więcej informacji na temat tworzenia i używania zasobów, zobacz [zasoby w aplikacjach klasycznych](../../resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../resources/index.md).</span></span>

6. <span data-ttu-id="4b4f6-126">Kompiluj i Wdróż swój formant.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-126">Compile and deploy your control.</span></span> <span data-ttu-id="4b4f6-127">Aby skompilować i wdrożyć `FirstControl,` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4b4f6-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>

    1. <span data-ttu-id="4b4f6-128">Zapisz kod w następującym przykładzie do pliku źródłowego (na przykład FirstControl.cs lub FirstControl. vb).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>

    2. <span data-ttu-id="4b4f6-129">Skompiluj kod źródłowy do zestawu i Zapisz go w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="4b4f6-130">Aby to osiągnąć, wykonaj następujące polecenie w katalogu, który zawiera plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         <span data-ttu-id="4b4f6-131">Opcja kompilatora `/t:library` informuje kompilator, że tworzony zestaw jest biblioteką (a nie plikiem wykonywalnym).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="4b4f6-132">Opcja `/out` określa ścieżkę i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="4b4f6-133">Opcja`/r` zawiera nazwę zestawów, do których odwołuje się kod.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="4b4f6-134">W tym przykładzie utworzysz prywatny zestaw, którego mogą używać tylko Twoje aplikacje.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="4b4f6-135">W związku z tym należy zapisać go w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="4b4f6-136">Aby uzyskać więcej informacji o pakowaniu i wdrażaniu kontrolki do dystrybucji, zobacz [wdrażanie](../../deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../deployment/index.md).</span></span>

<span data-ttu-id="4b4f6-137">Poniższy przykład pokazuje kod dla `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="4b4f6-138">Kontrolka jest zawarta w przestrzeni nazw `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="4b4f6-139">Przestrzeń nazw zawiera logiczne grupowanie typów pokrewnych.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="4b4f6-140">Formant można utworzyć w nowej lub istniejącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="4b4f6-141">W C#programie deklaracja `using` (w Visual Basic, `Imports`) umożliwia dostęp do typów z przestrzeni nazw bez używania w pełni kwalifikowanej nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="4b4f6-142">W poniższym przykładzie deklaracja `using` pozwala kodowi uzyskać dostęp do klasy <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> jako <xref:System.Windows.Forms.Control>, zamiast używać w pełni kwalifikowanej nazwy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="4b4f6-143">Używanie kontrolki niestandardowej w formularzu</span><span class="sxs-lookup"><span data-stu-id="4b4f6-143">Using the Custom Control on a Form</span></span>

<span data-ttu-id="4b4f6-144">Poniższy przykład pokazuje prosty formularz, który używa `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="4b4f6-145">Tworzy trzy wystąpienia `FirstControl`, z których każda ma inną wartość właściwości `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>

#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="4b4f6-146">Aby skompilować i uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="4b4f6-146">To compile and run this sample</span></span>

1. <span data-ttu-id="4b4f6-147">Zapisz kod w poniższym przykładzie do pliku źródłowego (SimpleForm.cs lub SimpleForms. vb).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>

2. <span data-ttu-id="4b4f6-148">Skompiluj kod źródłowy do zestawu wykonywalnego, wykonując następujące polecenie z katalogu, który zawiera plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     <span data-ttu-id="4b4f6-149">CustomWinControls. dll jest zestawem zawierającym klasę `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="4b4f6-150">Ten zestaw musi znajdować się w tym samym katalogu, co plik źródłowy dla formularza, który uzyskuje do niego dostęp (SimpleForm.cs lub SimpleForms. vb).</span><span class="sxs-lookup"><span data-stu-id="4b4f6-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>

3. <span data-ttu-id="4b4f6-151">Wykonaj SimpleForm. exe przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b4f6-151">Execute SimpleForm.exe using the following command.</span></span>

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a><span data-ttu-id="4b4f6-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b4f6-152">See also</span></span>

- [<span data-ttu-id="4b4f6-153">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b4f6-153">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="4b4f6-154">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b4f6-154">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
