---
title: 'Instrukcje: Utwórz Freezable tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: e0cc5d73f9b9f15fc02bf20a70c84da1a7c535c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671671"
---
# <a name="how-to-make-a-freezable-read-only"></a>Instrukcje: Utwórz Freezable tylko do odczytu
W tym przykładzie pokazano, jak wprowadzić <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego <xref:System.Windows.Freezable.Freeze%2A> metody.  
  
 Nie można zablokować <xref:System.Windows.Freezable> obiektu, jeśli jeden z następujących warunków jest `true` dotyczących obiektu:  
  
-   Ma ona animowane lub powiązania danych właściwości.  
  
-   Posiada właściwości, które są ustawiane przez zasób dynamiczny. Aby uzyskać więcej informacji o zasobach dynamicznej, zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie mogą być zablokowane.  
  
 Jeśli te warunki są `false` dla Twojego <xref:System.Windows.Freezable> obiektu, a nie zamierzasz go zmodyfikować, należy wziąć pod uwagę zawiesza się on do korzyści w zakresie wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush>, który jest typem <xref:System.Windows.Freezable> obiektu.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
