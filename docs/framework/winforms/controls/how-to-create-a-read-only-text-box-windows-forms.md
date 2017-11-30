---
title: 'Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9cf6064442c3b648116f98f98f169dac12e5e88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="77fc2-102">Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="77fc2-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="77fc2-103">Można edytować pole tekstowe formularzy systemu Windows można przekształcać w formancie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="77fc2-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="77fc2-104">Na przykład mogą być wyświetlane pole tekstowe wartość, która zwykle jest edytowane, ale nie może być aktualnie, ze względu na stan aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77fc2-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="77fc2-105">Aby utworzyć pole tekstowe tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="77fc2-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="77fc2-106">Ustaw <xref:System.Windows.Forms.TextBox> formantu <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="77fc2-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="77fc2-107">Z ustawioną właściwością `true`, użytkownicy mogą nadal przewiń i wyróżnianie tekstu w polu tekstowym bez możliwości zmiany.</span><span class="sxs-lookup"><span data-stu-id="77fc2-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="77fc2-108">A **kopiowania** polecenia będzie działać w polu tekstowym, ale **Wytnij** i **Wklej** polecenia nie są.</span><span class="sxs-lookup"><span data-stu-id="77fc2-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77fc2-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Właściwość ma wpływ tylko na interakcji z użytkownikiem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="77fc2-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="77fc2-110">Można nadal zmienić zawartości pola tekstowego programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> właściwości pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="77fc2-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fc2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77fc2-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="77fc2-112">Informacje o formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="77fc2-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="77fc2-113">Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="77fc2-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="77fc2-114">Porady: Tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="77fc2-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="77fc2-115">Porady: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="77fc2-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="77fc2-116">Porady: Zaznaczanie tekstu w oknach formantu TextBox formularzy</span><span class="sxs-lookup"><span data-stu-id="77fc2-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="77fc2-117">Porady: wyświetlanie wielu wierszy w oknach formantu TextBox formularzy</span><span class="sxs-lookup"><span data-stu-id="77fc2-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="77fc2-118">TextBox — formant</span><span class="sxs-lookup"><span data-stu-id="77fc2-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
