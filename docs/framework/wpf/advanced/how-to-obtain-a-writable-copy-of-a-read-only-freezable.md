---
title: "Jak uzyskać zapisywalną kopię Freezable tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6925e9322063d68d0d7f8c8e048eed254cd14ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
