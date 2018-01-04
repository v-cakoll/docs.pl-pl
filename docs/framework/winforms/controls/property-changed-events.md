---
title: "Zdarzenia zmiany właściwości"
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
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad22d77043f00ab0caaa6d8b08b6b0a9eef1fed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="property-changed-events"></a>Zdarzenia zmiany właściwości
Jeśli chcesz, aby formantu można wysłać powiadomienia, gdy właściwość o nazwie *PropertyName* zmiany, zdefiniuj zdarzenia o nazwie *PropertyName* `Changed` i metodę o nazwie `On` *PropertyName* `Changed` który wywołuje zdarzenie. Konwencja nazewnictwa w formularzach systemu Windows są dołączane słowo *zmienione* do nazwy właściwości. Typ delegata skojarzonego zdarzenia dla zdarzenia zmiany właściwości jest <xref:System.EventHandler>, a typ danych zdarzenia jest <xref:System.EventArgs>. Klasa podstawowa <xref:System.Windows.Forms.Control> definiuje wiele zdarzeń zmiany właściwości, takie jak <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>i inne. Aby uzyskać ogólne informacje o zdarzeniach, zobacz [zdarzenia](../../../../docs/standard/events/index.md) i [zdarzenia w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).  
  
 Zdarzenia zmiany właściwości są przydatne, ponieważ umożliwiają one konsumentów formantu można dołączyć procedury obsługi zdarzeń, które odpowiadają na zmiany. Jeśli formantu musi odpowiadać na zdarzenie zmiany właściwości, która zgłasza, Zastąp odpowiadającą jej `On` *PropertyName* `Changed` metody zamiast dołączanie delegata zdarzenia. Formant zazwyczaj odpowiada na zdarzenie zmiany właściwości, aktualizując inne właściwości lub ponownego narysowania niektórych lub wszystkich powierzchni do rysowania.  
  
 W poniższym przykładzie przedstawiono sposób `FlashTrackBar` kontrolki niestandardowej reaguje na niektóre zdarzenia zmiany właściwości, które dziedziczy on z <xref:System.Windows.Forms.Control>. Pełny przykład, zobacz [jak: utworzyć Windows formularze kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [Zdarzenia w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
