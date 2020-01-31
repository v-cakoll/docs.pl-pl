---
title: PrintPreviewControl, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741436"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> służy do wyświetlania elementu [PrintDocument](printdocument-component-windows-forms.md) , który będzie wyświetlany podczas drukowania. Ta kontrolka nie ma przycisków ani innych elementów interfejsu użytkownika, więc zazwyczaj używasz <xref:System.Windows.Forms.PrintPreviewControl> tylko wtedy, gdy chcesz napisać własny interfejs użytkownika w wersji zapoznawczej. Jeśli chcesz użyć standardowego interfejsu użytkownika, użyj kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>. Zobacz [Omówienie kontrolki PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md) , aby zapoznać się z omówieniem.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwość klucza kontrolki jest <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, która ustawia dokument do podglądu. Dokument musi być obiektem <xref:System.Drawing.Printing.PrintDocument>. Aby zapoznać się z omówieniem tworzenia dokumentów do drukowania, zobacz [Omówienie składnika PrintDocument](printdocument-component-overview-windows-forms.md) i [Obsługa drukowania Windows Forms](../advanced/windows-forms-print-support.md). Właściwości <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> określają liczbę stron wyświetlanych w poziomie i w pionie na formancie. Wygładzanie może sprawiać, że tekst wydaje się gładszy, ale może również spowodować spowolnienie wyświetlania. Aby go użyć, ustaw właściwość <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> na `true`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog, kontrolka — omówienie](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl, kontrolka](printpreviewcontrol-control-windows-forms.md)
- [Kontrolki i składniki okien dialogowych](dialog-box-controls-and-components-windows-forms.md)
