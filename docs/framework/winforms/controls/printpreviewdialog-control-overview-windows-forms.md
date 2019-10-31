---
title: PrintPreviewDialog — Informacje o formancie [Formularze systemu Windows]
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 670886956e1b348895862c117ccf9cf586bde8bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141220"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="a0c96-102">PrintPreviewDialog — informacje o formancie (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a0c96-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="a0c96-103">Kontrolka <xref:System.Windows.Forms.PrintPreviewDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym używanym do wyświetlania, jak [PrintDocument](printdocument-component-windows-forms.md) pojawi się po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="a0c96-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="a0c96-104">Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie zamiast konfigurować własne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a0c96-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="a0c96-105">Kontrolka zawiera przyciski do drukowania, powiększania, wyświetlania jednej lub wielu stron i zamykania okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="a0c96-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="a0c96-106">Właściwości i metody klucza</span><span class="sxs-lookup"><span data-stu-id="a0c96-106">Key properties and methods</span></span>

<span data-ttu-id="a0c96-107">Właściwość klucza kontrolki jest <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, która ustawia dokument do podglądu.</span><span class="sxs-lookup"><span data-stu-id="a0c96-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="a0c96-108">Dokument musi być obiektem <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="a0c96-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="a0c96-109">Aby wyświetlić okno dialogowe, należy wywołać jego metodę <xref:System.Windows.Forms.Form.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0c96-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="a0c96-110">Wygładzanie może sprawiać, że tekst wydaje się gładszy, ale może również spowodować spowolnienie wyświetlania. Aby go użyć, ustaw właściwość <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a0c96-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="a0c96-111">Niektóre właściwości są dostępne za pomocą <xref:System.Windows.Forms.PrintPreviewControl>, które <xref:System.Windows.Forms.PrintPreviewDialog> zawiera.</span><span class="sxs-lookup"><span data-stu-id="a0c96-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="a0c96-112">(Nie musisz dodawać tego <xref:System.Windows.Forms.PrintPreviewControl> do formularza; jest on automatycznie zawarty w <xref:System.Windows.Forms.PrintPreviewDialog> po dodaniu okna dialogowego do formularza). Przykłady właściwości dostępnych za pomocą <xref:System.Windows.Forms.PrintPreviewControl> są właściwościami <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, które określają liczbę stron wyświetlanych w poziomie i w pionie na formancie.</span><span class="sxs-lookup"><span data-stu-id="a0c96-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="a0c96-113">Możesz uzyskać dostęp do właściwości <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> jako `PrintPreviewDialog1.PrintPreviewControl.Columns` w Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` w wizualizacji C#lub `printPreviewDialog1->PrintPreviewControl->Columns` w wizualizacji. C++</span><span class="sxs-lookup"><span data-stu-id="a0c96-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="a0c96-114">PrintPreviewDialog wydajność</span><span class="sxs-lookup"><span data-stu-id="a0c96-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="a0c96-115">W następujących warunkach formant <xref:System.Windows.Forms.PrintPreviewDialog> jest zainicjowany bardzo wolno:</span><span class="sxs-lookup"><span data-stu-id="a0c96-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="a0c96-116">Używana jest drukarka sieciowa.</span><span class="sxs-lookup"><span data-stu-id="a0c96-116">A network printer is used.</span></span>
- <span data-ttu-id="a0c96-117">Preferencje użytkownika dotyczące tej drukarki, takie jak ustawienia dupleks, są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="a0c96-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="a0c96-118">W przypadku aplikacji uruchamianych w .NET Framework 4.5.2 można dodać następujący klucz do sekcji \<appSettings > pliku konfiguracji, aby zwiększyć wydajność inicjowania <xref:System.Windows.Forms.PrintPreviewDialog> kontroli:</span><span class="sxs-lookup"><span data-stu-id="a0c96-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="a0c96-119">Jeśli klucz `EnablePrintPreviewOptimization` jest ustawiony na inną wartość lub jeśli klucz nie istnieje, optymalizacja nie zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="a0c96-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="a0c96-120">W przypadku aplikacji uruchamianych w .NET Framework 4,6 lub nowszych wersjach można dodać następujący przełącznik do elementu [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w sekcji [\<Runtime >](../../configure-apps/file-schema/runtime/index.md) w pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="a0c96-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="a0c96-121">Jeśli przełącznik nie jest obecny lub jest ustawiony na inną wartość, optymalizacja nie zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="a0c96-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="a0c96-122">W przypadku użycia zdarzenia <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> w celu zmodyfikowania ustawień drukarki wydajność kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> nie zostanie zwiększona nawet po ustawieniu przełącznika konfiguracji optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="a0c96-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0c96-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0c96-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="a0c96-124">PrintPreviewControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a0c96-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="a0c96-125">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a0c96-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="a0c96-126">Kontrolki i składniki okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="a0c96-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
