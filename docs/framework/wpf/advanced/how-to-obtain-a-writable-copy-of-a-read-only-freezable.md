---
title: 'Instrukcje: Uzyskiwanie zapisywalnej kopii obiektu Freezable tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 910c5dada6ca82f68992722e4df6b35f9f7497c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206476"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Instrukcje: Uzyskiwanie zapisywalnej kopii obiektu Freezable tylko do odczytu
W tym przykładzie pokazano, jak używać <xref:System.Windows.Freezable.Clone%2A> metodę w celu utworzenia zapisywalną kopię tylko do odczytu <xref:System.Windows.Freezable>.  
  
 Po <xref:System.Windows.Freezable> obiekt jest oznaczony jako tylko do odczytu ("zamrożona"), nie można go modyfikować. Można jednak użyć <xref:System.Windows.Freezable.Clone%2A> metodę, aby sklonować można modyfikować zamrożonych obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład obejmuje tworzenie modyfikowalnych klonu zamrożone <xref:System.Windows.Media.SolidColorBrush> obiektu.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [Przegląd Obiekty Freezable](freezable-objects-overview.md)
- [— Tematy porad](base-elements-how-to-topics.md)
