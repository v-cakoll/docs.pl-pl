---
title: Przekazywanie adresu URI do środowiska wykonawczego systemu Windows
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5ce0d4ac2b95dc4d51e785e3a00026f56c13d2c
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047426"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="1fca2-102">Przekazywanie adresu URI do środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1fca2-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="1fca2-103">Metod środowiska wykonawczego Windows akceptuje tylko bezwzględne identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="1fca2-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="1fca2-104">Jeśli przekażesz względny identyfikator URI do [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1fca2-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="1fca2-105">Oto Dlaczego: kiedy używać [!INCLUDE[wrt](../../../includes/wrt-md.md)] w kodzie .NET Framework <xref:Windows.Foundation.Uri?displayProperty=nameWithType> klasa jest wyświetlany jako <xref:System.Uri?displayProperty=nameWithType> w technologii Intellisense.</span><span class="sxs-lookup"><span data-stu-id="1fca2-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="1fca2-106"><xref:System.Uri?displayProperty=nameWithType> Klasa umożliwia względne identyfikatory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> klasy nie jest.</span><span class="sxs-lookup"><span data-stu-id="1fca2-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="1fca2-107">To samo dotyczy metod udostępnianych w [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników.</span><span class="sxs-lookup"><span data-stu-id="1fca2-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="1fca2-108">Jeśli składnik udostępnia metodę, która przyjmuje identyfikator URI, podpis w kodzie zawiera <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1fca2-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fca2-109">Jednak użytkownikom składnika podpis zawiera <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1fca2-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fca2-110">Identyfikator URI, który jest przekazywany do składnika musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="1fca2-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="1fca2-111">W tym temacie pokazano, jak wykrywać bezwzględny identyfikator URI i jak go utworzyć przy odwoływaniu się do zasobu w pakiecie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1fca2-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="1fca2-112">Wykrywanie i używanie bezwzględnego identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="1fca2-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="1fca2-113">Użyj <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> właściwości, aby upewnić się, że identyfikator URI jest bezwzględny, przed przekazaniem go do [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1fca2-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="1fca2-114">Używanie tej właściwości jest bardziej efektywne niż wychwytywanie i obsługa <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1fca2-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="1fca2-115">Za pomocą bezwzględny identyfikator URI zasobu w pakiecie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1fca2-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="1fca2-116">Jeśli chcesz określić identyfikator URI zasobu, który zawiera pakiet aplikacji, możesz użyć `ms-appx` lub `ms-appx-web` schemat, aby utworzyć bezwzględny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="1fca2-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="1fca2-117">Poniższy przykład pokazuje, jak ustawić <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> właściwość <xref:Windows.UI.Xaml.Controls.WebView> kontroli i <xref:Windows.UI.Xaml.Controls.Image.Source%2A> właściwość <xref:Windows.UI.Xaml.Controls.Image> formantu do zasobów, które są zawarte w folderze o nazwie stron przy użyciu XAML i kodu.</span><span class="sxs-lookup"><span data-stu-id="1fca2-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="1fca2-118">Aby uzyskać więcej informacji na temat tych schematów, zobacz [schematy identyfikatorów URI](/windows/uwp/app-resources/uri-schemes) w Centrum deweloperów Windows.</span><span class="sxs-lookup"><span data-stu-id="1fca2-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fca2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fca2-119">See also</span></span>

- [<span data-ttu-id="1fca2-120">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1fca2-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
