---
title: "Porady: używanie klasy renderowania formantu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbf17ea84cb24d167975e6b918a0410a38c8ed3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-control-rendering-class"></a>Porady: używanie klasy renderowania formantu
W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Forms.ComboBoxRenderer> klasy do renderowania kontrolki pola kombi strzałkę listy rozwijanej. Przykład składa się z <xref:System.Windows.Forms.Control.OnPaint%2A> metody proste kontrolki niestandardowej. <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Właściwość jest używana do określenia, czy style wizualne są włączone w klienckim obszarze aplikacji systemu windows. Jeżeli style wizualne są aktywne, a następnie <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> strzałkę listy rozwijanej przy użyciu stylów wizualnych; spowoduje, że metoda w przeciwnym razie <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> spowoduje, że strzałkę listy rozwijanej w stylu klasycznym Windows metody.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Formant niestandardowy pochodną <xref:System.Windows.Forms.Control> klasy.  
  
-   A <xref:System.Windows.Forms.Form> obsługującego kontrolki niestandardowej.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Renderowanie kontrolek przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
