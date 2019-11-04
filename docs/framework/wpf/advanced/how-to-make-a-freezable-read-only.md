---
title: Jak utworzyć Freezable tylko do odczytu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460070"
---
# <a name="how-to-make-a-freezable-read-only"></a>Jak utworzyć Freezable tylko do odczytu
Ten przykład pokazuje, jak wykonać <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego metody <xref:System.Windows.Freezable.Freeze%2A>.  
  
 Nie można zablokować obiektu <xref:System.Windows.Freezable>, jeśli jeden z następujących warunków jest `true` o obiekcie:  
  
- Ma właściwości animowane lub powiązane z danymi.  
  
- Ma właściwości, które są ustawiane przez zasób dynamiczny. Aby uzyskać więcej informacji na temat zasobów dynamicznych, zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Zawiera <xref:System.Windows.Freezable> obiektów podrzędnych, które nie mogą być zamrożone.  
  
 Jeśli te warunki są `false` dla obiektu <xref:System.Windows.Freezable> i nie zamierzasz go modyfikować, rozważ zamarzanie go w celu uzyskania korzyści z wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiesza <xref:System.Windows.Media.SolidColorBrush>, który jest typem obiektu <xref:System.Windows.Freezable>.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiektów, zobacz [Omówienie obiektów Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Przegląd obiektów Freezable](freezable-objects-overview.md)
- [Tematy z instrukcjami](base-elements-how-to-topics.md)
