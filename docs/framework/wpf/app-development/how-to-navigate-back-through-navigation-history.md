---
title: 'Porady: poruszanie się wstecz historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 7266c9486524e962a859c34c9be5ab8f6d7bf7d5
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367917"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Porady: poruszanie się wstecz historii nawigacji
Ten przykład ilustruje sposób przejścia do wpisów na spód historii nawigacji.  
  
## <a name="example"></a>Przykład  
 Kod, który jest uruchomiony przez zawartość, która znajduje się w <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> przy użyciu <xref:System.Windows.Navigation.NavigationService>, lub [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] przejść wstecz w historii nawigacji, jeden wpis w danym momencie.  
  
 Po wstecz o jeden wpis wymaga najpierw sprawdzanie, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości przed przechodząc kopii jeden wpis, wywołując **GoBack** Metoda. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> jest wywoływane.
