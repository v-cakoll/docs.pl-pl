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
ms.openlocfilehash: 7152fb02abf430c0d0e27b82550e4006e3958e93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288891"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="8a70d-102">Przekazywanie adresu URI do środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8a70d-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="8a70d-103">Metody środowisko wykonawcze systemu Windows akceptują tylko bezwzględne identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="8a70d-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="8a70d-104">Jeśli przekażesz względny identyfikator URI do metody środowisko wykonawcze systemu Windows, <xref:System.ArgumentException> zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8a70d-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="8a70d-105">Oto dlaczego: w przypadku używania środowisko wykonawcze systemu Windows w kodzie .NET Framework, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Klasa jest wyświetlana jako <xref:System.Uri?displayProperty=nameWithType> technologia IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8a70d-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="8a70d-106"><xref:System.Uri?displayProperty=nameWithType>Klasa umożliwia względne identyfikatory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Klasa nie.</span><span class="sxs-lookup"><span data-stu-id="8a70d-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="8a70d-107">Dotyczy to również metod ujawnianych w składnikach środowisko wykonawcze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a70d-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="8a70d-108">Jeśli składnik uwidacznia metodę, która pobiera identyfikator URI, podpis w kodzie zawiera <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8a70d-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8a70d-109">Jednak w przypadku użytkowników składnika podpis obejmuje <xref:Windows.Foundation.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8a70d-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8a70d-110">Identyfikator URI, który jest przesyłany do składnika, musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="8a70d-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="8a70d-111">W tym temacie pokazano, jak wykryć bezwzględny identyfikator URI i jak utworzyć go podczas odwoływania się do zasobu w pakiecie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a70d-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="8a70d-112">Wykrywanie i używanie bezwzględnego identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="8a70d-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="8a70d-113">Użyj <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> właściwości, aby upewnić się, że identyfikator URI jest bezwzględny przed przekazaniem go do środowisko wykonawcze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a70d-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="8a70d-114">Używanie tej właściwości jest bardziej wydajne niż przechwytywanie i obsługa <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8a70d-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="8a70d-115">Używanie bezwzględnego identyfikatora URI dla zasobu w pakiecie aplikacji</span><span class="sxs-lookup"><span data-stu-id="8a70d-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="8a70d-116">Jeśli chcesz określić identyfikator URI zasobu, który zawiera pakiet aplikacji, możesz użyć `ms-appx` schematu lub, `ms-appx-web` Aby utworzyć bezwzględny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="8a70d-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="8a70d-117">Poniższy przykład pokazuje, jak ustawić <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> Właściwość dla <xref:Windows.UI.Xaml.Controls.WebView> kontrolki i <xref:Windows.UI.Xaml.Controls.Image.Source%2A> Właściwość <xref:Windows.UI.Xaml.Controls.Image> kontrolki na zasoby, które są zawarte w folderze o nazwie Pages, przy użyciu XAML i kodu.</span><span class="sxs-lookup"><span data-stu-id="8a70d-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="8a70d-118">Aby uzyskać więcej informacji o tych schematach, zobacz [schematy identyfikatorów URI](/windows/uwp/app-resources/uri-schemes) w centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a70d-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a70d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a70d-119">See also</span></span>

- [<span data-ttu-id="8a70d-120">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8a70d-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
