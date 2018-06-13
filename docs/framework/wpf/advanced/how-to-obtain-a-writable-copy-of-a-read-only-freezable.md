---
title: Jak uzyskać zapisywalną kopię Freezable tylko do odczytu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543624"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Jak uzyskać zapisywalną kopię Freezable tylko do odczytu
Ten przykład przedstawia sposób użycia <xref:System.Windows.Freezable.Clone%2A> metodę, aby utworzyć kopię zapisu tylko do odczytu <xref:System.Windows.Freezable>.  
  
 Po <xref:System.Windows.Freezable> obiekt jest oznaczony jako tylko do odczytu ("zablokowane"), nie można go modyfikować. Można jednak użyć <xref:System.Windows.Freezable.Clone%2A> metodę w celu utworzenia klonu można modyfikować obiektu zablokowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy modyfikowalną Sklonowanie zablokowane <xref:System.Windows.Media.SolidColorBrush> obiektu.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
