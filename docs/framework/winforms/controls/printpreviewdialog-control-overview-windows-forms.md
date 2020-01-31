---
title: PrintPreviewDialog — Informacje o formancie
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 6fb971493336cda1e04c720dd09147e650918c3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741410"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog — informacje o formancie (Windows Forms)

Kontrolka <xref:System.Windows.Forms.PrintPreviewDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym używanym do wyświetlania, jak [PrintDocument](printdocument-component-windows-forms.md) pojawi się po wydrukowaniu. Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie zamiast konfigurować własne okno dialogowe. Kontrolka zawiera przyciski do drukowania, powiększania, wyświetlania jednej lub wielu stron i zamykania okna dialogowego.

## <a name="key-properties-and-methods"></a>Właściwości i metody klucza

Właściwość klucza kontrolki jest <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, która ustawia dokument do podglądu. Dokument musi być obiektem <xref:System.Drawing.Printing.PrintDocument>. Aby wyświetlić okno dialogowe, należy wywołać jego metodę <xref:System.Windows.Forms.Form.ShowDialog%2A>. Wygładzanie może sprawiać, że tekst wydaje się gładszy, ale może również spowodować spowolnienie wyświetlania. Aby go użyć, ustaw właściwość <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> na `true`.

Niektóre właściwości są dostępne za pomocą <xref:System.Windows.Forms.PrintPreviewControl>, które <xref:System.Windows.Forms.PrintPreviewDialog> zawiera. (Nie musisz dodawać tego <xref:System.Windows.Forms.PrintPreviewControl> do formularza; jest on automatycznie zawarty w <xref:System.Windows.Forms.PrintPreviewDialog> po dodaniu okna dialogowego do formularza). Przykłady właściwości dostępnych za pomocą <xref:System.Windows.Forms.PrintPreviewControl> są właściwościami <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, które określają liczbę stron wyświetlanych w poziomie i w pionie na formancie. Możesz uzyskać dostęp do właściwości <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> jako `PrintPreviewDialog1.PrintPreviewControl.Columns` w Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` w wizualizacji C#lub `printPreviewDialog1->PrintPreviewControl->Columns` w wizualizacji. C++

## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog wydajność

W następujących warunkach formant <xref:System.Windows.Forms.PrintPreviewDialog> jest zainicjowany bardzo wolno:

- Używana jest drukarka sieciowa.
- Preferencje użytkownika dotyczące tej drukarki, takie jak ustawienia dupleks, są modyfikowane.

W przypadku aplikacji uruchamianych w .NET Framework 4.5.2 można dodać następujący klucz do sekcji \<appSettings > pliku konfiguracji, aby zwiększyć wydajność inicjowania <xref:System.Windows.Forms.PrintPreviewDialog> kontroli:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

Jeśli klucz `EnablePrintPreviewOptimization` jest ustawiony na inną wartość lub jeśli klucz nie istnieje, optymalizacja nie zostanie zastosowana.

W przypadku aplikacji uruchamianych w .NET Framework 4,6 lub nowszych wersjach można dodać następujący przełącznik do elementu [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w sekcji [\<Runtime >](../../configure-apps/file-schema/runtime/index.md) w pliku konfiguracji aplikacji:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Jeśli przełącznik nie jest obecny lub jest ustawiony na inną wartość, optymalizacja nie zostanie zastosowana.

W przypadku użycia zdarzenia <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> w celu zmodyfikowania ustawień drukarki wydajność kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> nie zostanie zwiększona nawet po ustawieniu przełącznika konfiguracji optymalizacji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl, kontrolka — omówienie](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog, kontrolka](printpreviewdialog-control-windows-forms.md)
- [Kontrolki i składniki okien dialogowych](dialog-box-controls-and-components-windows-forms.md)
