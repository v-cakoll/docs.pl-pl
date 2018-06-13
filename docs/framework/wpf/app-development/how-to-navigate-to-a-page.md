---
title: 'Porady: Przejdź na stronę'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 896287376979d40816e3937fff77b38bf71a62f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548392"
---
# <a name="how-to-navigate-to-a-page"></a>Porady: Przejdź na stronę
W tym przykładzie przedstawiono kilka sposobów, w których strona może zostać przesłane do z <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Przykład  
 Istnieje możliwość <xref:System.Windows.Navigation.NavigationWindow> można przejść do strony przy użyciu jednej z następujących czynności:  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A> Właściwości.  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Metody.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] może być względna lub bezwzględna. Aby uzyskać więcej informacji, zobacz [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.NavigationService>
