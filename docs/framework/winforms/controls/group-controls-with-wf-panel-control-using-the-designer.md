---
title: "Porady: grupowanie formantów z formantem panelu formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1d4a49f36ac294199871075a04b7e682bd5613b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Porady: grupowanie formantów z formantem panelu formularzy systemu Windows przy użyciu narzędzia Projektant
Formularze systemu Windows <xref:System.Windows.Forms.Panel> formanty są używane do grupowania inne formanty. Istnieją trzy powodów Grupowanie formantów. Jedna jest visual grupowanie elementów pokrewnych formularza dla interfejsu użytkownika wyczyść; inny jest programowe grupowania, przyciski radiowe na przykład; ostatni jest przenoszenie kontrolek jako jednostki w czasie projektowania.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-group-of-controls"></a>Aby utworzyć grupę formantów  
  
1.  Przeciągnij <xref:System.Windows.Forms.Panel> kontrolować z **formularzy systemu Windows** karcie przybornika do formularza.  
  
2.  Dodać inne formanty do panelu rysowania każdego wewnątrz panelu.  
  
     Jeśli masz istniejących formantów, które chcesz umieścić w panelu można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.Panel> kontroli, a następnie wklej je do panelu. Można również przeciągnij je do panelu.  
  
3.  (Opcjonalnie) Jeśli chcesz dodać obramowanie do panelu, ustaw jej <xref:System.Windows.Forms.BorderStyle> właściwości. Istnieją trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, i <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Zobacz też  
 [Panel — formant](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel — Informacje o formancie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Porady: Ustawianie tła panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
