---
title: PrintPreviewDialog — Informacje o formancie [Formularze systemu Windows]
ms.custom: ''
ms.date: 01/08/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e5602a8aa4c83eb8dad33dff31f2dc0e7e7858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Printpreviewdialog — informacje o formancie (formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.PrintPreviewDialog> formant jest używany do wyświetlania okno dialogowe wstępnie skonfigurowane jak [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) po wydrukowaniu. Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem zamiast konfigurować własne okno dialogowe. Formant zawiera przyciski do drukowania, powiększyć wyświetlania jednego lub wielu stron i zamknięcie okna dialogowego.  
  
## <a name="key-properties-and-methods"></a>Właściwości klucza i metody  
 Właściwość klucza formantu jest <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, który ustawia dokumentu, który ma zostać wyświetlony. Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu. Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.Form.ShowDialog%2A> metody. Wygładzanie można wprowadzić tekst płynny, ale można również ustawić wyświetlania wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> właściwości `true`.  
  
 Niektóre właściwości są dostępne za pośrednictwem <xref:System.Windows.Forms.PrintPreviewControl> który <xref:System.Windows.Forms.PrintPreviewDialog> zawiera. (Nie trzeba dodać to <xref:System.Windows.Forms.PrintPreviewControl> do formularza; jest on automatycznie zawarty w <xref:System.Windows.Forms.PrintPreviewDialog> po dodaniu okna dialogowego do formularza.) Przykłady dostępne za pośrednictwem właściwości <xref:System.Windows.Forms.PrintPreviewControl> są <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości, które określają liczba stron wyświetlanych w formancie poziomie i w pionie. Dostęp można uzyskać <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> właściwość jako `PrintPreviewDialog1.PrintPreviewControl.Columns` w języku Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` języka Visual C#, lub `printPreviewDialog1->PrintPreviewControl->Columns` w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>Printpreviewdialog — wydajności

W następujących warunkach <xref:System.Windows.Forms.PrintPreviewDialog> formant inicjuje bardzo wolno:

- Drukarki sieciowej jest używany.
- Preferencje użytkownika dotyczące tej drukarki, takie jak ustawienia dupleksu są modyfikowane.
  
Dla aplikacji działających na programie .NET Framework 4.5.2, można dodać następujący klucz \<appSettings > sekcji pliku konfiguracji, aby poprawić wydajność <xref:System.Windows.Forms.PrintPreviewDialog> kontroli inicjowania:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Jeśli `EnablePrintPreviewOptimization` jest ustawiona na dowolną inną wartość, lub jeśli klucz nie jest obecny, optymalizacja nie została zastosowana.

Dla aplikacji działających na .NET Framework 4.6 lub nowszy, można dodać do następującego przełącznika [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) sekcji w pliku konfiguracyjnym aplikacji:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Jeśli nie ma przełącznika lub jeśli ustawiono ją na inną wartość, optymalizacja nie została zastosowana. 

Jeśli używasz <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> zdarzeń, aby zmodyfikować ustawienia drukarki, wydajność <xref:System.Windows.Forms.PrintPreviewDialog> nie poprawi kontroli, nawet jeśli jest ustawiona przełącznik konfiguracji optymalizacji.  

## <a name="see-also"></a>Zobacz także  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [PrintPreviewControl, kontrolka — omówienie](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [PrintPreviewDialog, kontrolka](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Kontrolki i składniki okien dialogowych](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
