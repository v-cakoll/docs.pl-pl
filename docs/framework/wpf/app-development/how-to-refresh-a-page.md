---
title: 'Instrukcje: Odśwież stronę.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
ms.openlocfilehash: 71a71c91384a8905413358d023531afec23f2d41
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368288"
---
# <a name="how-to-refresh-a-page"></a>Instrukcje: Odśwież stronę.
W tym przykładzie przedstawiono sposób wywoływania <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> metodę, aby odświeżyć zawartość bieżącego <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> Odświeża zawartość bieżącego <xref:System.Windows.Navigation.NavigationWindow> ponowne załadowanie z jej źródła.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
