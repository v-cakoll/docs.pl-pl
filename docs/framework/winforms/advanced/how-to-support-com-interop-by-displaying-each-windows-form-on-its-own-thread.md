---
title: 'Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku'
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 90bbd7df45424f8513598e9d7439d8ae6bf6f52c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040310"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="d54d1-102">Instrukcje: Obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows w jego własnym wątku</span><span class="sxs-lookup"><span data-stu-id="d54d1-102">How to: Support COM interop by displaying each Windows Form on its own thread</span></span>

<span data-ttu-id="d54d1-103">Problemy ze współdziałaniem modelu COM można rozwiązać, wyświetlając formularz w pętli .NET Framework komunikatów, którą można utworzyć za pomocą <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d54d1-103">You can resolve COM interoperability problems by displaying your form on a .NET Framework message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d54d1-104">Aby formularz systemu Windows działał prawidłowo z aplikacji klienckiej modelu COM, należy uruchomić formularz w pętli komunikatów Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d54d1-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="d54d1-105">W tym celu należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="d54d1-105">To do this, use one of the following approaches:</span></span>

- <span data-ttu-id="d54d1-106"><xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Użyj metody, aby wyświetlić formularz systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d54d1-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="d54d1-107">Aby uzyskać więcej informacji, zobacz [jak: Obsługa międzyoperacyjności modelu COM przez wyświetlanie formularza systemu Windows przy](com-interop-by-displaying-a-windows-form-shadow.md)użyciu metody ShowDialog.</span><span class="sxs-lookup"><span data-stu-id="d54d1-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>

- <span data-ttu-id="d54d1-108">Wyświetl Każdy formularz systemu Windows w osobnym wątku.</span><span class="sxs-lookup"><span data-stu-id="d54d1-108">Display each Windows Form on a separate thread.</span></span>

<span data-ttu-id="d54d1-109">W programie Visual Studio jest dostępna szeroka obsługa tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d54d1-109">There is extensive support for this feature in Visual Studio.</span></span>

<span data-ttu-id="d54d1-110">Zobacz [również przewodnik: Obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))w jego własnym wątku.</span><span class="sxs-lookup"><span data-stu-id="d54d1-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="d54d1-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d54d1-111">Example</span></span>

<span data-ttu-id="d54d1-112">Poniższy przykład kodu pokazuje, jak wyświetlić formularz w osobnym wątku i wywołać <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodę, aby uruchomić Windows Forms pompę komunikatów na tym wątku.</span><span class="sxs-lookup"><span data-stu-id="d54d1-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="d54d1-113">Aby użyć tej metody, należy zorganizować wszystkie wywołania formularza z niezarządzanej aplikacji za pomocą <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d54d1-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>

<span data-ttu-id="d54d1-114">Takie podejście wymaga, aby każde wystąpienie formularza było uruchamiane we własnym wątku przy użyciu własnej pętli komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d54d1-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="d54d1-115">Na wątek nie może być uruchomiona więcej niż jedna pętla komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d54d1-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="d54d1-116">W związku z tym nie można zmienić pętli komunikatów aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="d54d1-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="d54d1-117">Można jednak zmodyfikować składnik .NET Framework, aby uruchomić nowy wątek, który używa własnej pętli komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d54d1-117">However, you can modify the .NET Framework component to start a new thread that uses its own message loop.</span></span>

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a><span data-ttu-id="d54d1-118">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="d54d1-118">Compile the code</span></span>

<span data-ttu-id="d54d1-119">`COMForm`Skompiluj, `Form1`, `COMWinform.dll`i `FormManager` , do zestawu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="d54d1-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="d54d1-120">Zarejestrowanie zestawu dla współdziałania z modelem COM przy użyciu jednej z metod opisanych w pakiecie [pakowanie zestawu dla modelu COM](../../interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="d54d1-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="d54d1-121">Teraz można używać zestawu i odpowiedniego pliku biblioteki typów (TLB) w aplikacjach niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d54d1-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="d54d1-122">Można na przykład użyć biblioteki typów jako odniesienia w projekcie wykonywalnym Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="d54d1-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54d1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d54d1-123">See also</span></span>

- [<span data-ttu-id="d54d1-124">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="d54d1-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="d54d1-125">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="d54d1-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="d54d1-126">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="d54d1-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="d54d1-127">Instrukcje: Obsługa międzyoperacyjności modelu COM przez wyświetlanie formularza systemu Windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="d54d1-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="d54d1-128">Przegląd formularzy Windows Forms i niezarządzanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="d54d1-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
