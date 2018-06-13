---
title: Jak powiązać z wyliczeniem
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 921f15a32eeb5ccb20e879466fcfee3233bbd29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554950"
---
# <a name="how-to-bind-to-an-enumeration"></a>Jak powiązać z wyliczeniem
W tym przykładzie pokazano, jak powiązać z wyliczeniem przez powiązanie do metody GetValues wyliczenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Controls.ListBox> Wyświetla listę <xref:System.Windows.HorizontalAlignment> wartości wyliczenia za pośrednictwem powiązania danych. <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button> są powiązane w taki sposób, że można zmienić <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość właściwości <xref:System.Windows.Controls.Button> , wybierając wartość w <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie z metodą](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
