---
title: 'Instrukcje: Uzyskaj zapisywalną kopię Freezable tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 2853b1e02e1223cbb2b6dff4acbddb0a41d882cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629959"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Instrukcje: Uzyskaj zapisywalną kopię Freezable tylko do odczytu
W tym przykładzie pokazano, jak używać <xref:System.Windows.Freezable.Clone%2A> metodę w celu utworzenia zapisywalną kopię tylko do odczytu <xref:System.Windows.Freezable>.  
  
 Po <xref:System.Windows.Freezable> obiekt jest oznaczony jako tylko do odczytu ("zamrożona"), nie można go modyfikować. Można jednak użyć <xref:System.Windows.Freezable.Clone%2A> metodę, aby sklonować można modyfikować zamrożonych obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład obejmuje tworzenie modyfikowalnych klonu zamrożone <xref:System.Windows.Media.SolidColorBrush> obiektu.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
