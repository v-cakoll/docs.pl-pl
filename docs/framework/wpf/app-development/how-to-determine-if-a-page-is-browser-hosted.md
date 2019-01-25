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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="91b82-102">Instrukcje: Określa, czy strona jest hostowana w przeglądarce</span><span class="sxs-lookup"><span data-stu-id="91b82-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="91b82-103">W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Controls.Page> znajduje się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="91b82-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91b82-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="91b82-104">Example</span></span>  
 <span data-ttu-id="91b82-105">A <xref:System.Windows.Controls.Page> może być niezależny od hosta, a w związku z tym, może być załadowany do kilku różnych typów hostów, w tym <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, albo w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="91b82-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="91b82-106">Może się to zdarzyć, gdy masz zestaw biblioteki, która zawiera co najmniej jednej strony, który jest przywoływany przez wiele autonomiczną i można przeglądać ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91b82-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="91b82-107">Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> do określenia, czy <xref:System.Windows.Controls.Page> znajduje się w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="91b82-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="91b82-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91b82-108">See also</span></span>
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
