---
title: "PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47bef441b01d8bdcf9a365c341005cff28c64f27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="d40a6-102">PrintPreviewControl — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="d40a6-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="d40a6-103">Formularze systemu Windows <xref:System.Windows.Forms.PrintPreviewControl> służy do wyświetlania [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) jak będzie wyglądać po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="d40a6-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="d40a6-104">Ten formant ma nie przyciski lub inne elementy interfejsu użytkownika, dlatego zazwyczaj używany <xref:System.Windows.Forms.PrintPreviewControl> tylko wtedy, gdy chcesz zapisać własnego interfejsu użytkownika podglądu wydruku.</span><span class="sxs-lookup"><span data-stu-id="d40a6-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="d40a6-105">Standardowy interfejs użytkownika, należy użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować; zobacz [printpreviewdialog — informacje o formancie](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) omówienie.</span><span class="sxs-lookup"><span data-stu-id="d40a6-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="d40a6-106">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="d40a6-106">Key Properties</span></span>  
 <span data-ttu-id="d40a6-107">Właściwość klucza formantu jest <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, który ustawia dokumentu, który ma zostać wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="d40a6-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="d40a6-108">Dokument musi być <xref:System.Drawing.Printing.PrintDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d40a6-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="d40a6-109">Omówienie tworzenia dokumentów do drukowania, zobacz [informacje o składniku PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) i [Obsługa drukowania formularzy systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="d40a6-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="d40a6-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> i <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> właściwości określają liczba stron wyświetlanych w formancie poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="d40a6-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="d40a6-111">Antialiasingu można wprowadzić tekst płynny, ale można również ustawić wyświetlania wolniejsze; Aby go użyć, należy ustawić <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="d40a6-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40a6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d40a6-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="d40a6-113">Printpreviewdialog — informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="d40a6-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="d40a6-114">Printpreviewcontrol — formant</span><span class="sxs-lookup"><span data-stu-id="d40a6-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="d40a6-115">Okno dialogowe formanty i składniki</span><span class="sxs-lookup"><span data-stu-id="d40a6-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
