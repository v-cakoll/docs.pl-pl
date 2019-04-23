---
title: PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122502"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.PrintPreviewControl> służy do wyświetlania [PrintDocument](printdocument-component-windows-forms.md) taką jaka będzie wyświetlana po wydrukowaniu. Ten formant ma żadnych przycisków lub inne elementy interfejsu użytkownika, dlatego zazwyczaj używasz <xref:System.Windows.Forms.PrintPreviewControl> tylko wtedy, gdy chcesz napisać własny interfejs użytkownika Podgląd wydruku. Standardowy interfejs użytkownika, użyć <xref:System.Windows.Forms.PrintPreviewDialog> formant; zobacz [printpreviewdialog — informacje o formancie](printpreviewdialog-control-overview-windows-forms.md) omówienie.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwość klucza jest <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, który ustawia dokumentów, których podgląd będzie wyświetlany. Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu. Omówienie tworzenia dokumentów do drukowania, zobacz [— informacje o składniku PrintDocument](printdocument-component-overview-windows-forms.md) i [obsługę drukowania formularzy Windows](../advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości określają liczbę stron wyświetlany poziomo i pionowo w kontrolce. Antyaliasing mogą wprowadzać tekst płynny, ale może również sprawić, że wyświetlana wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> właściwość `true`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog, kontrolka — omówienie](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl, kontrolka](printpreviewcontrol-control-windows-forms.md)
- [Kontrolki i składniki okien dialogowych](dialog-box-controls-and-components-windows-forms.md)
