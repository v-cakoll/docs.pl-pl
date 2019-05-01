---
title: 'Instrukcje: Poruszanie się wstecz w historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: c489a1593b3d1f22fe1ad6e648d3f8a3f7a6cd44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947787"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Instrukcje: Poruszanie się wstecz w historii nawigacji
Ten przykład ilustruje sposób przejścia do wpisów na spód historii nawigacji.  
  
## <a name="example"></a>Przykład  
 Kod, który jest uruchomiony przez zawartość, która znajduje się w <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> przy użyciu <xref:System.Windows.Navigation.NavigationService>, lub [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] przejść wstecz w historii nawigacji, jeden wpis w danym momencie.  
  
 Po wstecz o jeden wpis wymaga najpierw sprawdzanie, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości przed przechodząc kopii jeden wpis, wywołując **GoBack** Metoda. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> jest wywoływane.
