---
title: Aplikacje niezarządzane
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746366"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="0d274-102">Formularze systemu Windows i niezarządzane aplikacje</span><span class="sxs-lookup"><span data-stu-id="0d274-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="0d274-103">Windows Forms aplikacje i kontrolki mogą współdziałać z niezarządzanymi aplikacjami z pewnymi zastrzeżeniami.</span><span class="sxs-lookup"><span data-stu-id="0d274-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="0d274-104">W poniższych sekcjach opisano scenariusze i konfiguracje, które Windows Forms aplikacjami i kontrolami, oraz te, które nie są obsługiwane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="0d274-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d274-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0d274-105">In This Section</span></span>  
 [<span data-ttu-id="0d274-106">Przegląd formularzy Windows Forms i niezarządzanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="0d274-106">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="0d274-107">Zawiera ogólne informacje dotyczące sposobu użycia i implementacji formantów Windows Forms, które działają z niezarządzanymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="0d274-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="0d274-108">Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="0d274-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="0d274-109">Zawiera przykładowy kod, który pokazuje, jak używać metody <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> do uruchamiania formularza systemu Windows w niezarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d274-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="0d274-110">Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku</span><span class="sxs-lookup"><span data-stu-id="0d274-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="0d274-111">Zawiera przykładowy kod, który pokazuje, jak uruchomić formularz systemu Windows w jego własnym wątku.</span><span class="sxs-lookup"><span data-stu-id="0d274-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="0d274-112">Zobacz również [Przewodnik: obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows w jego własnym wątku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0d274-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0d274-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0d274-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="0d274-114">Służy do tworzenia oddzielnego wątku dla formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0d274-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="0d274-115">Uruchamia pętlę komunikatów dla wątku.</span><span class="sxs-lookup"><span data-stu-id="0d274-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="0d274-116">Kierowanie wywołań z niezarządzanej aplikacji do formularza.</span><span class="sxs-lookup"><span data-stu-id="0d274-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d274-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0d274-117">Related Sections</span></span>  
 [<span data-ttu-id="0d274-118">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="0d274-118">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="0d274-119">Zawiera ogólne informacje dotyczące używania typów .NET Framework w niezarządzanych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="0d274-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
