---
title: "PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d50e772cf870d47314a25347f4909367062ffb94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.PrintPreviewControl> służy do wyświetlania [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) jak będzie wyglądać po wydrukowaniu. Ten formant ma nie przyciski lub inne elementy interfejsu użytkownika, dlatego zazwyczaj używany <xref:System.Windows.Forms.PrintPreviewControl> tylko wtedy, gdy chcesz zapisać własnego interfejsu użytkownika podglądu wydruku. Standardowy interfejs użytkownika, należy użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować; zobacz [printpreviewdialog — informacje o formancie](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) omówienie.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwość klucza formantu jest <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, który ustawia dokumentu, który ma zostać wyświetlony. Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu. Omówienie tworzenia dokumentów do drukowania, zobacz [informacje o składniku PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) i [Obsługa drukowania formularzy systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości określają liczba stron wyświetlanych w formancie poziomie i w pionie. Antialiasingu można wprowadzić tekst płynny, ale można również ustawić wyświetlania wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> właściwości `true`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [PrintPreviewDialog, kontrolka — omówienie](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [PrintPreviewControl, kontrolka](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [Kontrolki i składniki okien dialogowych](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
