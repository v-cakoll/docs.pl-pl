---
title: 'Instrukcje: Utwórz Freezable tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 874724584b44c17ff6c01331295cfa1a60978d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360358"
---
# <a name="how-to-make-a-freezable-read-only"></a>Instrukcje: Utwórz Freezable tylko do odczytu
W tym przykładzie pokazano, jak wprowadzić <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego <xref:System.Windows.Freezable.Freeze%2A> metody.  
  
 Nie można zablokować <xref:System.Windows.Freezable> obiektu, jeśli jeden z następujących warunków jest `true` dotyczących obiektu:  
  
-   Ma ona animowane lub powiązania danych właściwości.  
  
-   Posiada właściwości, które są ustawiane przez zasób dynamiczny. Aby uzyskać więcej informacji o zasobach dynamicznej, zobacz [zasoby XAML](xaml-resources.md).  
  
-   Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie mogą być zablokowane.  
  
 Jeśli te warunki są `false` dla Twojego <xref:System.Windows.Freezable> obiektu, a nie zamierzasz go zmodyfikować, należy wziąć pod uwagę zawiesza się on do korzyści w zakresie wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush>, który jest typem <xref:System.Windows.Freezable> obiektu.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Przegląd obiektów Freezable](freezable-objects-overview.md)
- [Tematy z instrukcjami](base-elements-how-to-topics.md)
