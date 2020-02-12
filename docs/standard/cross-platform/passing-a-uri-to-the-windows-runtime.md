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
ms.openlocfilehash: 71d427c2d602efbd92dc0128b1fada85a987904a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123626"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Przekazywanie adresu URI do środowiska wykonawczego systemu Windows
Metody środowisko wykonawcze systemu Windows akceptują tylko bezwzględne identyfikatory URI. Jeśli przekazywany jest względny identyfikator URI do metody środowisko wykonawcze systemu Windows, zostanie zgłoszony wyjątek <xref:System.ArgumentException>. Oto dlaczego: w przypadku używania środowisko wykonawcze systemu Windows w kodzie .NET Framework, Klasa <xref:Windows.Foundation.Uri?displayProperty=nameWithType> pojawia się jako <xref:System.Uri?displayProperty=nameWithType> w IntelliSense. Klasa <xref:System.Uri?displayProperty=nameWithType> umożliwia względne identyfikatory URI, ale Klasa <xref:Windows.Foundation.Uri?displayProperty=nameWithType> nie. Dotyczy to również metod ujawnianych w składnikach środowisko wykonawcze systemu Windows. Jeśli składnik uwidacznia metodę, która pobiera identyfikator URI, podpis w kodzie zawiera <xref:System.Uri?displayProperty=nameWithType>. Jednak w przypadku użytkowników składnika podpis zawiera <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Identyfikator URI, który jest przesyłany do składnika, musi być bezwzględnym identyfikatorem URI.  
  
W tym temacie pokazano, jak wykryć bezwzględny identyfikator URI i jak utworzyć go podczas odwoływania się do zasobu w pakiecie aplikacji.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Wykrywanie i używanie bezwzględnego identyfikatora URI  
Użyj właściwości <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>, aby upewnić się, że identyfikator URI jest bezwzględny przed przekazaniem go do środowisko wykonawcze systemu Windows. Używanie tej właściwości jest bardziej wydajne niż przechwytywanie i obsługa wyjątku <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Używanie bezwzględnego identyfikatora URI dla zasobu w pakiecie aplikacji  
Jeśli chcesz określić identyfikator URI zasobu, który zawiera pakiet aplikacji, możesz użyć schematu `ms-appx` lub `ms-appx-web`, aby utworzyć bezwzględny identyfikator URI.  
  
Poniższy przykład pokazuje, jak ustawić właściwość <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> dla kontrolki <xref:Windows.UI.Xaml.Controls.WebView> i Właściwość <xref:Windows.UI.Xaml.Controls.Image.Source%2A> dla kontrolki <xref:Windows.UI.Xaml.Controls.Image> na zasoby, które są zawarte w folderze o nazwie Pages, przy użyciu XAML i kodu.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Aby uzyskać więcej informacji o tych schematach, zobacz [schematy identyfikatorów URI](/windows/uwp/app-resources/uri-schemes) w centrum deweloperów systemu Windows.  
  
## <a name="see-also"></a>Zobacz też

- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
