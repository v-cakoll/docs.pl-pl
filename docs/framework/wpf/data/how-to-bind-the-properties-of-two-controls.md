---
title: "Jak powiązać właściwości dwóch formantów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff3da19d33e747ec514de9cd24fa08ccd6ab13bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Jak powiązać właściwości dwóch formantów
W tym przykładzie pokazano, jak można powiązać z właściwością jeden formant skonkretyzowanym niż przy użyciu innego <xref:System.Windows.Data.Binding.ElementName%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób powiązania <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Canvas> do <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> właściwości <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 W tym przykładzie jest renderowany go wygląda następująco:  
  
 ![Kanwa z zielonym tłem](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Uwaga** właściwość target powiązania (w tym przykładzie <xref:System.Windows.Controls.Panel.Background%2A> właściwości) musi być właściwością zależności. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Określ źródło powiązania](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
