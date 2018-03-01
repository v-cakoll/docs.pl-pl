---
title: "PageSetupDialog — Informacje o składniku (Formularze systemu Windows)"
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
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd2162cd2b538b5c6277991fab0ce40762f6c07d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="9675e-102">PageSetupDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="9675e-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="9675e-103">Formularze systemu Windows <xref:System.Windows.Forms.PageSetupDialog> składnik jest wstępnie skonfigurowana okno dialogowe służy do określania szczegóły strony do wydruku w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="9675e-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="9675e-104">Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem dla użytkowników, aby ustawić preferencje strony zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="9675e-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="9675e-105">Można umożliwić użytkownikom ustawić obramowania i margines, nagłówki i stopki i orientacji pionowej lub poziomej.</span><span class="sxs-lookup"><span data-stu-id="9675e-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="9675e-106">Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9675e-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="9675e-107">Właściwości klucza i metody</span><span class="sxs-lookup"><span data-stu-id="9675e-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="9675e-108">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w celu wyświetlenia okna dialogowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9675e-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="9675e-109">Ten składnik zgłosił właściwości można ustawić, które dotyczą albo jednej strony (<xref:System.Drawing.Printing.PrintDocument> klasy) lub dokument (<xref:System.Drawing.Printing.PageSettings> klasy).</span><span class="sxs-lookup"><span data-stu-id="9675e-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="9675e-110">Ponadto <xref:System.Windows.Forms.PageSetupDialog> składnika może służyć do określenia ustawienia drukarki, które są przechowywane w <xref:System.Drawing.Printing.PrinterSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="9675e-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="9675e-111">Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.PageSetupDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9675e-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9675e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9675e-112">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="9675e-113">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="9675e-113">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
