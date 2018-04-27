---
title: Przekazywanie adresu URI do środowiska wykonawczego systemu Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: 10
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5ed49555b7d87973849f30a502a46e508b6323e7
ms.sourcegitcommit: 68b60d38043e50104ccc90c76f8599b1ffe18346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="bb850-102">Przekazywanie adresu URI do środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb850-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="bb850-103">Środowisko wykonawcze systemu Windows metody akceptuje tylko bezwzględny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="bb850-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="bb850-104">W przypadku przekazania względny identyfikator URI do [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="bb850-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="bb850-105">Powód: Jeśli używasz [!INCLUDE[wrt](../../../includes/wrt-md.md)] w kodzie .NET Framework <xref:Windows.Foundation.Uri?displayProperty=nameWithType> klasy jest wyświetlany jako <xref:System.Uri?displayProperty=nameWithType> w Intellisense.</span><span class="sxs-lookup"><span data-stu-id="bb850-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="bb850-106"><xref:System.Uri?displayProperty=nameWithType> Klasa umożliwia względne identyfikatory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> nie obsługuje klasy.</span><span class="sxs-lookup"><span data-stu-id="bb850-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="bb850-107">Dotyczy to również metody udostępnić w [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników.</span><span class="sxs-lookup"><span data-stu-id="bb850-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="bb850-108">Jeśli składnik udostępnia metodę, która ma identyfikator URI, obejmuje podpisu w kodzie <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb850-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bb850-109">Jednak użytkownikom składnika sygnatura obejmuje <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb850-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bb850-110">Identyfikator URI, który jest przekazywany do składnika musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="bb850-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="bb850-111">W tym temacie pokazano sposób utworzyć podczas odwoływania się do zasobu w pakiecie aplikacji oraz sposobu wykrywania bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="bb850-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="bb850-112">Wykrywanie i używanie bezwzględnym identyfikatorem URI</span><span class="sxs-lookup"><span data-stu-id="bb850-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="bb850-113">Użyj <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> właściwości, aby upewnić się, że identyfikator URI jest bezwzględny przed przekazaniem go do [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb850-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="bb850-114">Za pomocą tej właściwości jest bardziej efektywne niż przechwytywanie i obsługa <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="bb850-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="bb850-115">Przy użyciu bezwzględny identyfikator URI zasobu w pakiecie aplikacji</span><span class="sxs-lookup"><span data-stu-id="bb850-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="bb850-116">Jeśli chcesz określić identyfikator URI dla zasobu, który zawiera pakiet aplikacji, możesz użyć `ms-appx` lub `ms-appx-web` systemu do utworzenia bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="bb850-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="bb850-117">Poniższy przykład przedstawia sposób ustawiania [źródła](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) właściwość [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) kontroli i [źródła](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) właściwość [obrazu](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) kontroli z zasobami, które znajdują się w folderze o nazwie stron, używając XAML i kodem.</span><span class="sxs-lookup"><span data-stu-id="bb850-117">The following example shows how to set the [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="bb850-118">Aby uzyskać więcej informacji o tych systemów, zobacz [schematy identyfikatorów URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) w Centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb850-118">For more information about these schemes, see [URI schemes](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb850-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb850-119">See Also</span></span>  
 [<span data-ttu-id="bb850-120">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb850-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
