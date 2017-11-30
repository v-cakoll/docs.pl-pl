---
title: "Porady: stosowanie przycinania za pomocą obszaru"
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
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b57ffa91a41900e10aa921bd42509b1288134ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-clipping-with-a-region"></a>Porady: stosowanie przycinania za pomocą obszaru
Jedna z właściwości obiektu <xref:System.Drawing.Graphics> klasy jest obszar przycinania. Rysowanie wszystkie wykonywane przez dany <xref:System.Drawing.Graphics> obiektu jest ograniczony do obszar przycinania na tym <xref:System.Drawing.Graphics> obiektu. Można ustawić obszar przycinania przez wywołanie metody <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy ścieżki, która składa się z jednego wielokąta. Następnie kod tworzy regionu, w oparciu o tej ścieżce. Region jest przekazywana do <xref:System.Drawing.Graphics.SetClip%2A> metody <xref:System.Drawing.Graphics> obiektu, a następnie dwa ciągi są rysowane.  
  
 Na poniższej ilustracji przedstawiono przyciętą ciągów.  
  
 ![Klip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Regiony w GDI +](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Używanie regionów](../../../../docs/framework/winforms/advanced/using-regions.md)
