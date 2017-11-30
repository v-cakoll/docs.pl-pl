---
title: "ColorDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f3a25c601e46c18a30755a15131bba03669a2ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="bcb1a-102">ColorDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="bcb1a-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="bcb1a-103">Formularze systemu Windows <xref:System.Windows.Forms.ColorDialog> składnik jest wstępnie skonfigurowana okno dialogowe, które umożliwia użytkownikowi wybieranie koloru z palety i dodać do tej palety kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="bcb1a-104">To okno dialogowe tego samego widoczne w innych aplikacji systemu Windows, aby wybrać kolorów.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="bcb1a-105">Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="bcb1a-106">Kolor wybrany w oknie dialogowym jest zwracany w <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="bcb1a-107">Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `false`, przycisk "Definiuj kolory niestandardowe" jest wyłączona, a użytkownik jest ograniczony do wstępnie zdefiniowanych kolorów w palecie.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="bcb1a-108">Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać symulowanych kolorów.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="bcb1a-109">Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bcb1a-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb1a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcb1a-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="bcb1a-111">Colordialog — składnik</span><span class="sxs-lookup"><span data-stu-id="bcb1a-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="bcb1a-112">Okno dialogowe formanty i składniki</span><span class="sxs-lookup"><span data-stu-id="bcb1a-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="bcb1a-113">Porady: Zmienianie wyglądu składnika ColorDialog formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bcb1a-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
