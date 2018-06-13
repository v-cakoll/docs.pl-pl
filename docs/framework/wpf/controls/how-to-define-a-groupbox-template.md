---
title: Jak zdefiniować szablon GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: ed66d51e87a25f74e646d0d535ac9e4ee9c8a056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551139"
---
# <a name="how-to-define-a-groupbox-template"></a>Jak zdefiniować szablon GroupBox
W tym przykładzie pokazano, jak utworzyć szablon <xref:System.Windows.Controls.GroupBox> formantu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GroupBox> szablon formantu przy użyciu <xref:System.Windows.Controls.Grid> kontroli dla układu. Szablon używa <xref:System.Windows.Controls.BorderGapMaskConverter> do definiowania obramowania <xref:System.Windows.Controls.GroupBox> tak, aby obramowania nie może zasłaniać <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> zawartości.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GroupBox>  
 [Porada GroupBox — tematy](http://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
