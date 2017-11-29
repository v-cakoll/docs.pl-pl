---
title: "Jak określić, czy Freezable jest zamrożony"
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
helpviewer_keywords: Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47fb0a871c3792450386c440629ead1ee3fbecdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Jak określić, czy Freezable jest zamrożony
W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Freezable> obiektu jest zablokowany. Jeśli użytkownik próbuje zmodyfikować zablokowane <xref:System.Windows.Freezable> obiekt zgłasza <xref:System.InvalidOperationException>. Aby uniknąć generowania tego wyjątku, użyj <xref:System.Windows.Freezable.IsFrozen%2A> właściwość <xref:System.Windows.Freezable> obiektem, aby określić, czy jest zablokowana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush> i sprawdza ją przy użyciu <xref:System.Windows.Freezable.IsFrozen%2A> właściwości w celu określenia, czy jest zablokowana.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
