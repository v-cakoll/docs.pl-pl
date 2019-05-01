---
title: 'Instrukcje: Powiązywanie z wyliczeniem'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021014"
---
# <a name="how-to-bind-to-an-enumeration"></a>Instrukcje: Powiązywanie z wyliczeniem
W tym przykładzie pokazano, jak powiązać z wyliczeniem przez powiązanie metoda GetValues wyliczania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Controls.ListBox> wyświetlana jest lista <xref:System.Windows.HorizontalAlignment> wartości wyliczenia za pomocą powiązania danych. <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button> są powiązane w taki sposób, że można zmienić <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość właściwości <xref:System.Windows.Controls.Button> , wybierając wartość w <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązywanie z metodą](how-to-bind-to-a-method.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
