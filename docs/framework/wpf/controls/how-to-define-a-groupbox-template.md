---
title: Jak zdefiniować szablon GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: a47ce896be4d1c38147584dd80b1bc841737d526
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062509"
---
# <a name="how-to-define-a-groupbox-template"></a>Jak zdefiniować szablon GroupBox
W tym przykładzie pokazano, jak utworzyć szablon dla <xref:System.Windows.Controls.GroupBox> kontroli.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GroupBox> szablonu kontrolki przy użyciu <xref:System.Windows.Controls.Grid> kontroli dla układu. Szablon używa <xref:System.Windows.Controls.BorderGapMaskConverter> do definiowania obramowania <xref:System.Windows.Controls.GroupBox> tak, aby obramowania nie mogą zasłaniać <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> zawartości.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GroupBox>  
 [Tematy porad GroupBox](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
