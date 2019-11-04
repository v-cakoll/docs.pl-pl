---
title: Jak powiązać z wyliczeniem
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454440"
---
# <a name="how-to-bind-to-an-enumeration"></a>Jak powiązać z wyliczeniem
Ten przykład pokazuje, jak powiązać z wyliczeniem przez powiązanie z metodą GetValues wyliczenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Controls.ListBox> wyświetla listę <xref:System.Windows.HorizontalAlignment> wartości wyliczenia za pomocą powiązania danych. <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button> są powiązane, aby można było zmienić wartość właściwości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.Button> przez wybranie wartości z <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązywanie z metodą](how-to-bind-to-a-method.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
