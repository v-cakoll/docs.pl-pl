---
title: "Jak utworzyć Freezable tylko do odczytu"
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
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c407a2fcccfbda29ba23f63ba6ae71302c734d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-freezable-read-only"></a>Jak utworzyć Freezable tylko do odczytu
W tym przykładzie pokazano, jak utworzyć <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego <xref:System.Windows.Freezable.Freeze%2A> metody.  
  
 Nie można zablokować <xref:System.Windows.Freezable> obiektu, jeśli którykolwiek z następujących warunków jest `true` o obiektu:  
  
-   Ma on animowany lub właściwości powiązany z danymi.  
  
-   Ma właściwości, które są ustawiane przez zasobu dynamicznego. Aby uzyskać więcej informacji o zasobach dynamicznej, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie może być zablokowany.  
  
 Jeśli te warunki są `false` dla Twojego <xref:System.Windows.Freezable> obiektu, a nie zamierzasz go zmodyfikować, należy wziąć pod uwagę zamrażanie go do korzyści wydajności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush>, który jest typem <xref:System.Windows.Freezable> obiektu.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
