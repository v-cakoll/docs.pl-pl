---
title: 'Porady: odświeżanie strony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
ms.openlocfilehash: 27735450360206e0a15ecae00cc9d45f93e4e838
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546533"
---
# <a name="how-to-refresh-a-page"></a>Porady: odświeżanie strony
W tym przykładzie przedstawiono sposób wywoływania <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> metody w celu odświeżenia bieżącej zawartości w <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> Odświeża zawartość bieżącego <xref:System.Windows.Navigation.NavigationWindow> ponownego załadowania od źródła.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
