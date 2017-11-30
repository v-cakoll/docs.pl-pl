---
title: "Porady: stosowanie testowania trafień za pomocą obszaru"
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
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: adc55d137a5578dbe8649afa02ab8525d4913cd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Porady: stosowanie testowania trafień za pomocą obszaru
Celem testowania trafień jest ustalenie, czy kursor znajduje się nad danego obiektu, takie jak ikony lub przycisku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy region w kształcie plus przez tworzenie złożenie dwóch regionach prostokątny. Przyjęto założenie, że zmienna `point` zawiera lokalizację najnowszych kliknij. Kod sprawdza, czy `point` znajduje się w regionie w kształcie plus. Jeśli punkt znajduje się w regionie (trafienie), region jest wypełniony nieprzezroczyste pędzla czerwony. W przeciwnym razie region jest wypełniony półprzezroczystych pędzli czerwony.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Region>  
 [Regiony w GDI +](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Porady: stosowanie przycinania za pomocą obszaru](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
