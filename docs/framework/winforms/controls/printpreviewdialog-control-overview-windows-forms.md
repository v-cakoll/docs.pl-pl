---
title: PrintPreviewDialog — Informacje o formancie [Formularze systemu Windows]
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aad8673051b22db1df6d525094394dd2a43285ca
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711281"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Printpreviewdialog — informacje o formancie (formularze Windows)
Formularze Windows <xref:System.Windows.Forms.PrintPreviewDialog> sterowania to wstępnie skonfigurowane okno dialogowe umożliwia wyświetlenie jak [PrintDocument](printdocument-component-windows-forms.md) pojawią się po wydrukowaniu. Użyj go w ramach aplikacji opartych na Windows jako proste rozwiązanie zamiast konfigurować własne okno dialogowe. Kontrolka zawiera przyciski do drukowania, powiększania, wyświetlanie jednego lub wielu stronach i zamyka okno dialogowe.  
  
## <a name="key-properties-and-methods"></a>Kluczowe właściwości i metody  
 Właściwość klucza jest <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, który ustawia dokumentów, których podgląd będzie wyświetlany. Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu. Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.Form.ShowDialog%2A> metody. Wygładzanie można wprowadzać tekst płynny, ale może również sprawić, że wyświetlana wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> właściwość `true`.  
  
 Niektóre właściwości są dostępne za pośrednictwem <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> zawiera. (Nie trzeba dodać to <xref:System.Windows.Forms.PrintPreviewControl> do formularza; jest on automatycznie zawarta w <xref:System.Windows.Forms.PrintPreviewDialog> po dodaniu okna dialogowego do formularza.) Przykłady dostępnych za pośrednictwem właściwości <xref:System.Windows.Forms.PrintPreviewControl> są <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości, które określają liczbę stron wyświetlany poziomo i pionowo w kontrolce. Możesz uzyskać dostęp <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> właściwość jako `PrintPreviewDialog1.PrintPreviewControl.Columns` w języku Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` w elemencie wizualnym C#, lub `printPreviewDialog1->PrintPreviewControl->Columns` w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>Printpreviewdialog — wydajność

W następujących warunkach <xref:System.Windows.Forms.PrintPreviewDialog> kontroli inicjuje bardzo wolno:

- Drukarki sieciowej jest używany.
- Preferencje użytkownika dotyczące drukarki, takie jak ustawienia dupleksu są modyfikowane.
  
Dla aplikacji działających w .NET Framework 4.5.2, można dodać następujący klucz do \<appSettings > sekcji pliku konfiguracji w celu zwiększenia wydajności <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować inicjowania:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Jeśli `EnablePrintPreviewOptimization` jest ustawiona na jakąkolwiek inną wartość lub jeśli klucz nie jest obecny, optymalizacja nie ma zastosowania.

Dla aplikacji działających w .NET Framework 4.6 lub nowszej wersji, można dodać następującego przełącznika do [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) sekcja pliku konfiguracji aplikacji:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Jeśli przełącznik nie jest obecny lub jest ustawiona na jakąkolwiek inną wartość, optymalizacja nie została zastosowana. 

Jeśli używasz <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> zdarzenie, aby zmodyfikować ustawienia drukarki, wydajność <xref:System.Windows.Forms.PrintPreviewDialog> nie poprawi kontroli, nawet jeśli jest ustawiona na przełącznik konfiguracji optymalizacji.  

## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl, kontrolka — omówienie](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog, kontrolka](printpreviewdialog-control-windows-forms.md)
- [Kontrolki i składniki okien dialogowych](dialog-box-controls-and-components-windows-forms.md)
