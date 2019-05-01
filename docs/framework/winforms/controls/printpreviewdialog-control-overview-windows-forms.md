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
ms.openlocfilehash: 961b3c852f60a0917707bef07d4e26fc4215acca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012558"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="cc67f-102">Printpreviewdialog — informacje o formancie (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="cc67f-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="cc67f-103">Formularze Windows <xref:System.Windows.Forms.PrintPreviewDialog> sterowania to wstępnie skonfigurowane okno dialogowe umożliwia wyświetlenie jak [PrintDocument](printdocument-component-windows-forms.md) pojawią się po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="cc67f-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="cc67f-104">Użyj go w ramach aplikacji opartych na Windows jako proste rozwiązanie zamiast konfigurować własne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="cc67f-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="cc67f-105">Kontrolka zawiera przyciski do drukowania, powiększania, wyświetlanie jednego lub wielu stronach i zamyka okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="cc67f-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="cc67f-106">Kluczowe właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="cc67f-106">Key properties and methods</span></span>

<span data-ttu-id="cc67f-107">Właściwość klucza jest <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, który ustawia dokumentów, których podgląd będzie wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="cc67f-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="cc67f-108">Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc67f-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="cc67f-109">Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.Form.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cc67f-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="cc67f-110">Wygładzanie można wprowadzać tekst płynny, ale może również sprawić, że wyświetlana wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="cc67f-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="cc67f-111">Niektóre właściwości są dostępne za pośrednictwem <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> zawiera.</span><span class="sxs-lookup"><span data-stu-id="cc67f-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="cc67f-112">(Nie trzeba dodać to <xref:System.Windows.Forms.PrintPreviewControl> do formularza; jest on automatycznie zawarta w <xref:System.Windows.Forms.PrintPreviewDialog> po dodaniu okna dialogowego do formularza.) Przykłady dostępnych za pośrednictwem właściwości <xref:System.Windows.Forms.PrintPreviewControl> są <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości, które określają liczbę stron wyświetlany poziomo i pionowo w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="cc67f-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="cc67f-113">Możesz uzyskać dostęp <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> właściwość jako `PrintPreviewDialog1.PrintPreviewControl.Columns` w języku Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` w elemencie wizualnym C#, lub `printPreviewDialog1->PrintPreviewControl->Columns` w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc67f-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="cc67f-114">Printpreviewdialog — wydajność</span><span class="sxs-lookup"><span data-stu-id="cc67f-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="cc67f-115">W następujących warunkach <xref:System.Windows.Forms.PrintPreviewDialog> kontroli inicjuje bardzo wolno:</span><span class="sxs-lookup"><span data-stu-id="cc67f-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="cc67f-116">Drukarki sieciowej jest używany.</span><span class="sxs-lookup"><span data-stu-id="cc67f-116">A network printer is used.</span></span>
- <span data-ttu-id="cc67f-117">Preferencje użytkownika dotyczące drukarki, takie jak ustawienia dupleksu są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="cc67f-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="cc67f-118">Dla aplikacji działających w .NET Framework 4.5.2, można dodać następujący klucz do \<appSettings > sekcji pliku konfiguracji w celu zwiększenia wydajności <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować inicjowania:</span><span class="sxs-lookup"><span data-stu-id="cc67f-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="cc67f-119">Jeśli `EnablePrintPreviewOptimization` jest ustawiona na jakąkolwiek inną wartość lub jeśli klucz nie jest obecny, optymalizacja nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="cc67f-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="cc67f-120">Dla aplikacji działających w .NET Framework 4.6 lub nowszej wersji, można dodać następującego przełącznika do [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) sekcja pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="cc67f-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="cc67f-121">Jeśli przełącznik nie jest obecny lub jest ustawiona na jakąkolwiek inną wartość, optymalizacja nie została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="cc67f-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="cc67f-122">Jeśli używasz <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> zdarzenie, aby zmodyfikować ustawienia drukarki, wydajność <xref:System.Windows.Forms.PrintPreviewDialog> nie poprawi kontroli, nawet jeśli jest ustawiona na przełącznik konfiguracji optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="cc67f-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc67f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc67f-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="cc67f-124">PrintPreviewControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="cc67f-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="cc67f-125">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="cc67f-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="cc67f-126">Kontrolki i składniki okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="cc67f-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
