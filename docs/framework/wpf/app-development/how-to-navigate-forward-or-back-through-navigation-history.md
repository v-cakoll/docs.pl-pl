---
title: 'Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 00a41fcf85583ec0d081a2fa099f3a77cfcd2900
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625357"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji
Ten przykład ilustruje sposób przejścia do przodu i Wstecz w historii nawigacji dla wpisów.  
  
## <a name="example"></a>Przykład  
 Kod, który jest uruchamiany z zawartości w następujących hostów można przejść do przodu lub Wstecz w historii nawigacji, jeden wpis w danym momencie.  
  
- <xref:System.Windows.Navigation.NavigationWindow> za pomocą <xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame> za pomocą <xref:System.Windows.Navigation.NavigationService>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Zanim przejdziesz do przodu o jedną pozycję, musisz najpierw sprawdzić, czy znajdują się wpisy w historii przeglądania do przodu, sprawdzając **CanGoForward** właściwości. Aby przejść do przodu o jedną pozycję, należy wywołać **GoForward** metody. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Zanim można nawigować trybu jednego wpisu, musisz najpierw sprawdzić, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości. Aby przejść z powrotem jeden wpis, należy wywołać **GoBack** metody. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Jeśli wywołasz **GoForward**, i nie ma żadnych wpisów w historii przeglądania do przodu, lub jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> zgłaszany.
