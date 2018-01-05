---
title: "Porady: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 415ffebbcf196a163932b1b83e32a6128f0bf1a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="28bf7-102">Porady: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="28bf7-102">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>
<span data-ttu-id="28bf7-103">Można rozwiązać problemy ze współdziałaniem składnik modelu COM. wyświetlanie w formularzu systemu Windows [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, który jest tworzony przy użyciu <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="28bf7-103">You can resolve Component Object Model (COM) interoperability problems by displaying your Windows Form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which is created by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="28bf7-104">Aby formularz działał prawidłowo, od aplikacji klienckiej COM, należy uruchomić je na pętli komunikatów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="28bf7-104">To make a form work correctly from a COM client application, you must run it on a Windows Forms message loop.</span></span> <span data-ttu-id="28bf7-105">Aby to zrobić, użyj jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="28bf7-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="28bf7-106">Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza systemu Windows;</span><span class="sxs-lookup"><span data-stu-id="28bf7-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form;</span></span>  
  
-   <span data-ttu-id="28bf7-107">Wyświetlania każdego formularza systemu Windows w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="28bf7-107">Display each Windows Form on a separate thread.</span></span> <span data-ttu-id="28bf7-108">Aby uzyskać więcej informacji, zobacz [porady: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span><span class="sxs-lookup"><span data-stu-id="28bf7-108">For more information, see [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="28bf7-109">Procedura</span><span class="sxs-lookup"><span data-stu-id="28bf7-109">Procedure</span></span>  
 <span data-ttu-id="28bf7-110">Przy użyciu <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda może być Najprostszym sposobem wyświetlenia formularza na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, ponieważ podejścia, wymaga co najmniej kod do implementacji.</span><span class="sxs-lookup"><span data-stu-id="28bf7-110">Using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method can be the easiest way to display a form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop because, of all the approaches, it requires the least code to implement.</span></span>  
  
 <span data-ttu-id="28bf7-111"><xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Metody wstrzymuje pętli komunikatów niezarządzanej aplikacji i wyświetla formularza jako okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="28bf7-111">The <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method suspends the unmanaged application's message loop and displays the form as a dialog box.</span></span> <span data-ttu-id="28bf7-112">Ponieważ pętli komunikatów w aplikacji hosta zostało zawieszone, <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda tworzy nowy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów do przetwarzania komunikatów formularza.</span><span class="sxs-lookup"><span data-stu-id="28bf7-112">Because the host application's message loop has been suspended, the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method creates a new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop to process the form's messages.</span></span>  
  
 <span data-ttu-id="28bf7-113">Wadą korzystania <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda to, że formularz zostanie otwarty jako modalne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="28bf7-113">The disadvantage of using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method is that the form will be opened as a modal dialog box.</span></span> <span data-ttu-id="28bf7-114">To zachowanie blokuje interfejs użytkownika (UI) w aplikacji wywołującej przy otwartym formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="28bf7-114">This behavior blocks any user interface (UI) in the calling application while the Windows Form is open.</span></span> <span data-ttu-id="28bf7-115">Gdy użytkownik zamyka formularz, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] komunikatów pętla zostanie zamknięty i komunikat starsza aplikacja pętli uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="28bf7-115">When the user exits the form, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop closes and the earlier application's message loop starts running again.</span></span>  
  
 <span data-ttu-id="28bf7-116">Można utworzyć biblioteki klas w formularzach systemu Windows, który ma metodę wyświetlenie formularza i późniejszego kompilowania biblioteki klas dla modelu COM interop.</span><span class="sxs-lookup"><span data-stu-id="28bf7-116">You can create a class library in Windows Forms which has a method to show the form, and then build the class library for COM interop.</span></span> <span data-ttu-id="28bf7-117">Można użyć tego pliku DLL z języka Visual Basic 6.0 lub Microsoft Foundation Classes (MFC) i przy użyciu dowolnego z tych środowisk można wywołać <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza.</span><span class="sxs-lookup"><span data-stu-id="28bf7-117">You can use this DLL file from Visual Basic 6.0 or Microsoft Foundation Classes (MFC), and from either of these environments you can call the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the form.</span></span>  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="28bf7-118">Aby obsługa międzyoperacyjności modelu COM za pomocą wyświetlania formularzy systemu windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="28bf7-118">To support COM interop by displaying a windows form with the ShowDialog method</span></span>  
  
-   <span data-ttu-id="28bf7-119">Zamień wszystkie wywołania <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> metody wywołania <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metody w Twojej [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] składnika.</span><span class="sxs-lookup"><span data-stu-id="28bf7-119">Replace all calls to the <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> method with calls to the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method in your [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bf7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28bf7-120">See Also</span></span>  
 [<span data-ttu-id="28bf7-121">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="28bf7-121">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="28bf7-122">Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku</span><span class="sxs-lookup"><span data-stu-id="28bf7-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [<span data-ttu-id="28bf7-123">Formularze Windows Forms i niezarządzane aplikacje</span><span class="sxs-lookup"><span data-stu-id="28bf7-123">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
