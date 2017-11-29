---
title: 'Porady: ukrywanie formantu w czasie wykonywania'
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
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 310750df0786eb07158909eb5e322369d157d1cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Porady: ukrywanie formantu w czasie wykonywania
Brak godziny, kiedy warto utworzyć kontrolkę użytkownika, która jest niewidoczna w czasie wykonywania. Na przykład formant, który jest zegar alarm może być niewidoczna z wyjątkiem przypadków, gdy został podawania alarm. Łatwo jest to osiągane przez ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwości. Jeśli <xref:System.Windows.Forms.Control.Visible%2A> właściwość jest `true`, formantu będą wyświetlane jako standardowa. Jeśli `false`, formantu zostanie ukryta. Mimo że kod formantu mogą nadal działać podczas niewidoczne, nie będzie możliwość interakcji z formantem za pomocą interfejsu użytkownika. Jeśli chcesz utworzyć niewidocznym formancie nadal odpowiada interakcja z użytkownikiem (na przykład kliknięcie myszą), należy utworzyć przezroczystego formantu. Aby uzyskać więcej informacji, zobacz [nadanie przezroczystego tła formantu](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Aby ukrywanie formantu w czasie wykonywania  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Visible%2A> właściwości `false`.  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Porady: zapewniają przezroczystego tła formantu](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
