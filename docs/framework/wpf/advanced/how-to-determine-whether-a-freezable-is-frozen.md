---
title: 'Instrukcje: Określanie, czy obiekt Freezable jest zamrożony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 6a63862d35f2c40289ea6445eb3dab8a2abe4a61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197064"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Instrukcje: Określanie, czy obiekt Freezable jest zamrożony
W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Freezable> obiektu jest zablokowane. Jeśli spróbujesz zmodyfikować zamrożone <xref:System.Windows.Freezable> obiekt, w wyniku weryfikacji zgłasza wyjątek <xref:System.InvalidOperationException>. Aby uniknąć, zostanie zgłoszony wyjątek, należy użyć <xref:System.Windows.Freezable.IsFrozen%2A> właściwość <xref:System.Windows.Freezable> obiektu, aby ustalić, czy jest zablokowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush> i sprawdza ją za pomocą <xref:System.Windows.Freezable.IsFrozen%2A> właściwości w celu określenia, czy jest zablokowane.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Przegląd obiektów Freezable](freezable-objects-overview.md)
- [Tematy z instrukcjami](base-elements-how-to-topics.md)
