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
# <a name="passing-a-uri-to-the-windows-runtime"></a>Przekazywanie adresu URI do środowiska wykonawczego systemu Windows
Metody środowisko wykonawcze systemu Windows akceptują tylko bezwzględne identyfikatory URI. Jeśli przekażesz względny identyfikator URI do metody środowisko wykonawcze systemu Windows, <xref:System.ArgumentException> zostanie zgłoszony wyjątek. Oto dlaczego: w przypadku używania środowisko wykonawcze systemu Windows w kodzie .NET Framework, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Klasa jest wyświetlana jako <xref:System.Uri?displayProperty=nameWithType> technologia IntelliSense. <xref:System.Uri?displayProperty=nameWithType>Klasa umożliwia względne identyfikatory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Klasa nie. Dotyczy to również metod ujawnianych w składnikach środowisko wykonawcze systemu Windows. Jeśli składnik uwidacznia metodę, która pobiera identyfikator URI, podpis w kodzie zawiera <xref:System.Uri?displayProperty=nameWithType> . Jednak w przypadku użytkowników składnika podpis obejmuje <xref:Windows.Foundation.Uri?displayProperty=nameWithType> . Identyfikator URI, który jest przesyłany do składnika, musi być bezwzględnym identyfikatorem URI.  
  
W tym temacie pokazano, jak wykryć bezwzględny identyfikator URI i jak utworzyć go podczas odwoływania się do zasobu w pakiecie aplikacji.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Wykrywanie i używanie bezwzględnego identyfikatora URI  
Użyj <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> właściwości, aby upewnić się, że identyfikator URI jest bezwzględny przed przekazaniem go do środowisko wykonawcze systemu Windows. Używanie tej właściwości jest bardziej wydajne niż przechwytywanie i obsługa <xref:System.ArgumentException> wyjątku.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Używanie bezwzględnego identyfikatora URI dla zasobu w pakiecie aplikacji  
Jeśli chcesz określić identyfikator URI zasobu, który zawiera pakiet aplikacji, możesz użyć `ms-appx` schematu lub, `ms-appx-web` Aby utworzyć bezwzględny identyfikator URI.  
  
Poniższy przykład pokazuje, jak ustawić <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> Właściwość dla <xref:Windows.UI.Xaml.Controls.WebView> kontrolki i <xref:Windows.UI.Xaml.Controls.Image.Source%2A> Właściwość <xref:Windows.UI.Xaml.Controls.Image> kontrolki na zasoby, które są zawarte w folderze o nazwie Pages, przy użyciu XAML i kodu.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Aby uzyskać więcej informacji o tych schematach, zobacz [schematy identyfikatorów URI](/windows/uwp/app-resources/uri-schemes) w centrum deweloperów systemu Windows.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](support-for-windows-store-apps-and-windows-runtime.md)
