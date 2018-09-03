---
title: Formularze systemu Windows i niezarządzane aplikacje
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: bc0c848d1c92871dacab93497c674645f3ac83fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463942"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="7ea51-102">Formularze systemu Windows i niezarządzane aplikacje</span><span class="sxs-lookup"><span data-stu-id="7ea51-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="7ea51-103">Aplikacje Windows Forms i formanty może współpracować z niezarządzanych aplikacji za pomocą niektóre zastrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="7ea51-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="7ea51-104">Poniżej opisano scenariusze i konfiguracje obsługujące aplikacje i formanty Windows Forms oraz te, które nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="7ea51-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ea51-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7ea51-105">In This Section</span></span>  
 [<span data-ttu-id="7ea51-106">Przegląd formularzy Windows Forms i niezarządzanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="7ea51-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="7ea51-107">Udostępnia ogólne informacje o sposobie używania i zaimplementowania kontrolek Windows Forms, współpracujących z niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ea51-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="7ea51-108">Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="7ea51-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="7ea51-109">Zawiera przykładowy kod, który pokazuje, jak używać <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę, aby uruchomić formularza Windows w niezarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ea51-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="7ea51-110">Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku</span><span class="sxs-lookup"><span data-stu-id="7ea51-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="7ea51-111">Zawiera przykładowy kod, który pokazuje, jak uruchomić formularza Windows w jego własnym wątku.</span><span class="sxs-lookup"><span data-stu-id="7ea51-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="7ea51-112">Zobacz też [wskazówki: Obsługa międzyoperacyjności modelu COM, wyświetlanie każdego formularzu Windows w jego własnej wątku](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7ea51-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ea51-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7ea51-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="7ea51-114">Użyty do utworzenia oddzielnego wątku dla formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="7ea51-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="7ea51-115">Uruchamia pętli komunikatów dla wątku.</span><span class="sxs-lookup"><span data-stu-id="7ea51-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="7ea51-116">Organizuje wywołania z niezarządzanych aplikacji do formularza.</span><span class="sxs-lookup"><span data-stu-id="7ea51-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7ea51-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7ea51-117">Related Sections</span></span>  
 [<span data-ttu-id="7ea51-118">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="7ea51-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="7ea51-119">Udostępnia ogólne informacje o sposobie używania typów programu .NET Framework w aplikacjach niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7ea51-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
