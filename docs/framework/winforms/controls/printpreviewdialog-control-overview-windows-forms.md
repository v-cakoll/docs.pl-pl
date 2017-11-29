---
title: "PrintPreviewDialog — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c898dc24c9a4418e3af45fce507e6befcf905a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.PrintPreviewDialog> formant jest używany do wyświetlania okno dialogowe wstępnie skonfigurowane jak [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) po wydrukowaniu. Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem zamiast konfigurować własne okno dialogowe. Formant zawiera przyciski do drukowania, powiększyć wyświetlania jednego lub wielu stron i zamknięcie okna dialogowego.  
  
## <a name="key-properties-and-methods"></a>Właściwości klucza i metody  
 Właściwość klucza formantu jest <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, który ustawia dokumentu, który ma zostać wyświetlony. Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu. Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.Form.ShowDialog%2A> metody. Wygładzanie można wprowadzić tekst płynny, ale można również ustawić wyświetlania wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> właściwości `true`.  
  
 Niektóre właściwości są dostępne za pośrednictwem <xref:System.Windows.Forms.PrintPreviewControl> który <xref:System.Windows.Forms.PrintPreviewDialog> zawiera. (Nie trzeba dodać to <xref:System.Windows.Forms.PrintPreviewControl> do formularza; jest on automatycznie zawarty w <xref:System.Windows.Forms.PrintPreviewDialog> po dodaniu okna dialogowego do formularza.) Przykłady dostępne za pośrednictwem właściwości <xref:System.Windows.Forms.PrintPreviewControl> są <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości, które określają liczba stron wyświetlanych w formancie poziomie i w pionie. Dostęp można uzyskać <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> właściwość jako `PrintPreviewDialog1.PrintPreviewControl.Columns` w [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` w [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], lub `printPreviewDialog1->PrintPreviewControl->Columns` w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [Printpreviewcontrol — informacje o formancie](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [Printpreviewdialog — formant](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Okno dialogowe formanty i składniki](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
