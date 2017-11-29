---
title: "Formularze systemu Windows i niezarządzane aplikacje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8166ab6a69ce9a774e83e6dbc7278a41805f7a83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="689d2-102">Formularze systemu Windows i niezarządzane aplikacje</span><span class="sxs-lookup"><span data-stu-id="689d2-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="689d2-103">Aplikacji formularzy systemu Windows i formantów może współdziałać z niezarządzanych aplikacji, z niektórych ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="689d2-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="689d2-104">W poniższych sekcjach opisano scenariusze i konfiguracje obsługujące aplikacje i formantów formularzy systemu Windows oraz te, które nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="689d2-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="689d2-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="689d2-105">In This Section</span></span>  
 [<span data-ttu-id="689d2-106">Formularze systemu Windows i niezarządzanych aplikacji — omówienie</span><span class="sxs-lookup"><span data-stu-id="689d2-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="689d2-107">Udostępnia ogólne informacje o sposobie używania i implementować formanty formularzy systemu Windows, które współpracują z niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="689d2-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="689d2-108">Porady: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="689d2-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="689d2-109">Zawiera przykładowy kod, który przedstawia sposób użycia <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę do uruchomienia w formularzu systemu Windows w niezarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="689d2-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="689d2-110">Porady: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku</span><span class="sxs-lookup"><span data-stu-id="689d2-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="689d2-111">Zawiera przykładowy kod, który pokazuje sposób uruchamiania formularza systemu Windows w jego własnym wątku.</span><span class="sxs-lookup"><span data-stu-id="689d2-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="689d2-112">Zobacz też [wskazówki: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="689d2-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="689d2-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="689d2-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="689d2-114">Pozwala utworzyć oddzielnym wątku dla formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="689d2-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="689d2-115">Uruchamia Pętla wiadomości dla wątku.</span><span class="sxs-lookup"><span data-stu-id="689d2-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="689d2-116">Marshals wywołania z niezarządzanych aplikacji z formularzem.</span><span class="sxs-lookup"><span data-stu-id="689d2-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="689d2-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="689d2-117">Related Sections</span></span>  
 [<span data-ttu-id="689d2-118">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="689d2-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="689d2-119">Udostępnia ogólne informacje o sposobie używania typów .NET Framework w niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="689d2-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
