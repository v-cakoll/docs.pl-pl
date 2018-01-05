---
title: "Porady: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60e52bc1486f74bdce44062a4ac861032b7b660c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="ea35a-102">Porady: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku</span><span class="sxs-lookup"><span data-stu-id="ea35a-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="ea35a-103">Można rozwiązać problemy współdziałania COM za pomocą wyświetlania formularza na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, które można tworzyć przy użyciu <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ea35a-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ea35a-104">Aby poprawnie z aplikacji klienckiej COM służbowy formularza systemu Windows, należy uruchomić formularza w pętli komunikatów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ea35a-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="ea35a-105">Aby to zrobić, użyj jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="ea35a-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="ea35a-106">Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ea35a-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="ea35a-107">Aby uzyskać więcej informacji, zobacz [porady: Obsługa międzyoperacyjności z modelem COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="ea35a-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="ea35a-108">Wyświetlania każdego formularza systemu Windows w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="ea35a-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="ea35a-109">Brak kompleksową obsługę tej funkcji w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea35a-109">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="ea35a-110">Zobacz też [wskazówki: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ea35a-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea35a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea35a-111">Example</span></span>  
 <span data-ttu-id="ea35a-112">Poniższy przykład kodu pokazuje sposób wyświetlania formularza w oddzielnym wątku i wywołanie <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodę, aby uruchomić przekazywanie komunikatów formularzy systemu Windows na tym wątku.</span><span class="sxs-lookup"><span data-stu-id="ea35a-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="ea35a-113">Aby użyć tej metody, należy kierować wezwań do formularza z niezarządzanych aplikacji przy użyciu <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ea35a-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="ea35a-114">Ta metoda wymaga każde wystąpienie formularza działa przy użyciu własnego pętli komunikatów w jego własnym wątku.</span><span class="sxs-lookup"><span data-stu-id="ea35a-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="ea35a-115">Nie może mieć więcej niż jeden pętli komunikatów uruchomiona na wątek.</span><span class="sxs-lookup"><span data-stu-id="ea35a-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="ea35a-116">W związku z tym nie można zmienić pętli komunikatów aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="ea35a-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="ea35a-117">Jednak można zmodyfikować [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] składnika można rozpocząć nowego wątku, który używa własnego pętli komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ea35a-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea35a-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ea35a-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ea35a-119">Kompiluj `COMForm`, `Form1`, i `FormManager` typów w zestawie o nazwie `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="ea35a-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="ea35a-120">Zarejestrować zestawu dla międzyoperacyjności z modelem COM za pomocą jednej z metod opisanych w [pakowanie zestawu dla modelu COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="ea35a-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="ea35a-121">Można teraz używać zestawu i jego odpowiedni plik biblioteki (.tlb) typu w niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea35a-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="ea35a-122">Na przykład można użyć biblioteki typów jako odwołanie w Visual Basic 6.0 projekt wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="ea35a-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea35a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea35a-123">See Also</span></span>  
 [<span data-ttu-id="ea35a-124">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="ea35a-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="ea35a-125">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="ea35a-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [<span data-ttu-id="ea35a-126">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="ea35a-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="ea35a-127">Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="ea35a-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [<span data-ttu-id="ea35a-128">Przegląd formularzy Windows Forms i niezarządzanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="ea35a-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
