---
title: 'Instrukcje: nawigowanie do strony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 25a0dbbc609c7b6f8f2878d2068e61e492a59c7e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582537"
---
# <a name="how-to-navigate-to-a-page"></a>Instrukcje: nawigowanie do strony
Ten przykład ilustruje kilka sposobów, w których można przechodzić do strony z <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Przykład  
 Możliwe jest <xref:System.Windows.Navigation.NavigationWindow> przechodzenie do strony przy użyciu jednego z następujących elementów:  
  
- Właściwość <xref:System.Windows.Navigation.NavigationWindow.Source%2A>.  
  
- Metoda <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> Uniform Resource Identifier (URI) może być względna lub bezwzględna. Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
