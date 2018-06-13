---
title: Jak poruszać się w przód i wstecz w historii nawigacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546269"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Jak poruszać się w przód i wstecz w historii nawigacji
W tym przykładzie przedstawiono sposób przejdź do wpisów w historii przeglądania do przodu i do tyłu.  
  
## <a name="example"></a>Przykład  
 Kod uruchamiany z zawartości w następujące hosty można przejść do przodu i do tyłu za pośrednictwem historii nawigacji, jeden wpis w czasie.  
  
-   <xref:System.Windows.Navigation.NavigationWindow> Za pomocą <xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame> Za pomocą <xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Zanim przejdziesz do przodu jednego wpisu, musisz najpierw sprawdzić, czy wpisy w historii przeglądania do przodu sprawdzając **CanGoForward** właściwości. Aby przejść do przodu jednego wpisu, należy wywołać **GoForward** metody. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Zanim można przejść trybu jednego wpisu, musisz najpierw sprawdzić, czy wpisy w historii nawigacji Wstecz sprawdzając **CanGoBack** właściwości. Aby przejść wstecz jednego wpisu, należy wywołać **GoBack** metody. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Jeśli wywołujesz **GoForward**, i nie ma żadnych wpisów w historii przeglądania do przodu, lub jeśli wywołujesz **GoBack**, i nie ma żadnych wpisów w historii nawigacji Wstecz <xref:System.InvalidOperationException> jest generowany.
