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
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="574d1-102">PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="574d1-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="574d1-103">Formularze systemu Windows <xref:System.Windows.Forms.PrintPreviewControl> służy do wyświetlania [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) jak będzie wyglądać po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="574d1-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="574d1-104">Ten formant ma nie przyciski lub inne elementy interfejsu użytkownika, dlatego zazwyczaj używany <xref:System.Windows.Forms.PrintPreviewControl> tylko wtedy, gdy chcesz zapisać własnego interfejsu użytkownika podglądu wydruku.</span><span class="sxs-lookup"><span data-stu-id="574d1-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="574d1-105">Standardowy interfejs użytkownika, należy użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować; zobacz [printpreviewdialog — informacje o formancie](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) omówienie.</span><span class="sxs-lookup"><span data-stu-id="574d1-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="574d1-106">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="574d1-106">Key Properties</span></span>  
 <span data-ttu-id="574d1-107">Właściwość klucza formantu jest <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, który ustawia dokumentu, który ma zostać wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="574d1-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="574d1-108">Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="574d1-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="574d1-109">Omówienie tworzenia dokumentów do drukowania, zobacz [informacje o składniku PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) i [Obsługa drukowania formularzy systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="574d1-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="574d1-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości określają liczba stron wyświetlanych w formancie poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="574d1-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="574d1-111">Antialiasingu można wprowadzić tekst płynny, ale można również ustawić wyświetlania wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="574d1-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="574d1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="574d1-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="574d1-113">PrintPreviewDialog, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="574d1-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="574d1-114">PrintPreviewControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="574d1-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="574d1-115">Kontrolki i składniki okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="574d1-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
