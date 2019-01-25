---
title: 'Instrukcje: Określa, czy strona jest hostowana w przeglądarce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: aa2aa36e4f887c4fa02314f7834e2a46268c8ff9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661298"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Instrukcje: Określa, czy strona jest hostowana w przeglądarce
W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Controls.Page> znajduje się w przeglądarce.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.Page> może być niezależny od hosta, a w związku z tym, może być załadowany do kilku różnych typów hostów, w tym <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, albo w przeglądarce. Może się to zdarzyć, gdy masz zestaw biblioteki, która zawiera co najmniej jednej strony, który jest przywoływany przez wiele autonomiczną i można przeglądać ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostowania aplikacji.  
  
 Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> do określenia, czy <xref:System.Windows.Controls.Page> znajduje się w przeglądarce.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
