---
title: 'Instrukcje: Powiąż właściwości dwóch formantów'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: f3355969d0f12f0f3ed9b49bdb7efa6913c5e4c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372103"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Instrukcje: Powiąż właściwości dwóch formantów
W tym przykładzie pokazano, jak powiązać z innego przy użyciu właściwości jeden formant skonkretyzowany <xref:System.Windows.Data.Binding.ElementName%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Canvas> do <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> Właściwość <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Podczas renderowania w tym przykładzie wygląda następująco:  
  
 ![Kanwa zielonym tle](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Uwaga** właściwość target powiązania (w tym przykładzie <xref:System.Windows.Controls.Panel.Background%2A> właściwość) musi mieć właściwość zależności. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](data-binding-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Określanie obiektu źródłowego powiązania](how-to-specify-the-binding-source.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
