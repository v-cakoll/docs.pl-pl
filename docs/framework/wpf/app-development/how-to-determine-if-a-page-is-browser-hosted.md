---
title: 'Instrukcje: ustalanie, czy strona jest hostowana w przeglądarce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424688"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Instrukcje: ustalanie, czy strona jest hostowana w przeglądarce
W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Controls.Page> jest hostowana w przeglądarce.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Page> może być hostem niezależny od i, w związku z tym, może być ładowany do kilku różnych typów hostów, w tym <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>lub przeglądarki. Taka sytuacja może wystąpić, gdy istnieje zestaw biblioteki, który zawiera co najmniej jedną stronę, do której odwołuje się wiele autonomicznych i umożliwia przeglądaniaych aplikacji hosta (XBAP).  
  
 Poniższy przykład ilustruje sposób użycia <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>, aby określić, czy <xref:System.Windows.Controls.Page> jest hostowana w przeglądarce.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
