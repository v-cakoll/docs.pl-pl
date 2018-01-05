---
title: "Przekazywanie adresu URI do środowiska wykonawczego systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78ba02fa227bd5c10337da0ef8b65ceab476c1ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Przekazywanie adresu URI do środowiska wykonawczego systemu Windows
Środowisko wykonawcze systemu Windows metody akceptuje tylko bezwzględny identyfikator URI. W przypadku przekazania względny identyfikator URI do [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody <xref:System.ArgumentException> wyjątku. Powód: Jeśli używasz [!INCLUDE[wrt](../../../includes/wrt-md.md)] w kodzie .NET Framework [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) klasy jest wyświetlany jako <xref:System.Uri?displayProperty=nameWithType> w Intellisense. <xref:System.Uri?displayProperty=nameWithType> Klasa umożliwia względne identyfikatory URI, ale [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) nie obsługuje klasy. Dotyczy to również metody udostępnić w [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników. Jeśli składnik udostępnia metodę, która ma identyfikator URI, obejmuje podpisu w kodzie <xref:System.Uri?displayProperty=nameWithType>. Jednak użytkownikom składnika sygnatura obejmuje [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376). Identyfikator URI, który jest przekazywany do składnika musi być bezwzględnym identyfikatorem URI.  
  
 W tym temacie pokazano sposób utworzyć podczas odwoływania się do zasobu w pakiecie aplikacji oraz sposobu wykrywania bezwzględnym identyfikatorem URI.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Wykrywanie i używanie bezwzględnym identyfikatorem URI  
 Użyj <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> właściwości, aby upewnić się, że identyfikator URI jest bezwzględny przed przekazaniem go do [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Za pomocą tej właściwości jest bardziej efektywne niż przechwytywanie i obsługa <xref:System.ArgumentException> wyjątku.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Przy użyciu bezwzględny identyfikator URI zasobu w pakiecie aplikacji  
 Jeśli chcesz określić identyfikator URI dla zasobu, który zawiera pakiet aplikacji, możesz użyć `ms-appx` lub `ms-appx-web` systemu do utworzenia bezwzględnym identyfikatorem URI.  
  
 Poniższy przykład przedstawia sposób ustawiania [źródła](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) właściwość [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) kontroli i [źródła](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) właściwość [obrazu](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) kontroli z zasobami, które znajdują się w folderze o nazwie stron, używając XAML i kodem.  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Aby uzyskać więcej informacji o tych systemów, zobacz [schematy identyfikatorów URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) w Centrum deweloperów systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
