---
title: 'Porady: przechodzenie wstecz przez historii nawigacji'
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
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c715bda86fe6a4a010d80000db89619fc8bf8b7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Porady: przechodzenie wstecz przez historii nawigacji
W tym przykładzie przedstawiono sposób przejdź do pozycji na spód historii nawigacji.  
  
## <a name="example"></a>Przykład  
 Kod, który działa z zawartości, która jest obsługiwana w <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> użyj <xref:System.Windows.Navigation.NavigationService>, lub [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] można przejść za pośrednictwem historii nawigacji, jeden wpis w czasie.  
  
 Nawigacyjnego ponownie jeden wpis wymaga najpierw sprawdzanie, czy wpisy w historii nawigacji Wstecz, sprawdzając **CanGoBack** właściwości, zanim Nawigacja kopii jednego wpisu, wywołując **GoBack** Metoda. Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Jeśli należy wywołać **GoBack**, i nie ma żadnych wpisów w historii nawigacji Wstecz <xref:System.InvalidOperationException> jest wywoływane.
