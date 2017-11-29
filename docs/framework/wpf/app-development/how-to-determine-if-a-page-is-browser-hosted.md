---
title: "Porady: Określa, czy strona jest obsługiwane w przeglądarce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1da46596bf48d9648830d20758647be753f128fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Porady: Określa, czy strona jest obsługiwane w przeglądarce
W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Controls.Page> znajduje się w przeglądarce.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.Page> może być niezależny od hosta i, w związku z tym może być załadowany do wielu różnych typów hostów, w tym <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, lub w przeglądarce. Może się to zdarzyć, jeśli masz w zestawie biblioteki, która zawiera jedną lub więcej stron, odwołuje się wiele autonomicznych i można przeglądać ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostowania aplikacji.  
  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> można określić, czy <xref:System.Windows.Controls.Page> znajduje się w przeglądarce.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
