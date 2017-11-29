---
title: "Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a4141a27a3b195dbb747a827d2bd9426a948f83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="9be43-102">Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="9be43-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="9be43-103">Czasami może chcesz umieścić znaki cudzysłowu ("") w ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="9be43-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="9be43-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="9be43-104">For example:</span></span>  
  
 <span data-ttu-id="9be43-105">Użytkownik nazywany "Wymagają Traktuj!"</span><span class="sxs-lookup"><span data-stu-id="9be43-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="9be43-106">Alternatywnie, można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako stała.</span><span class="sxs-lookup"><span data-stu-id="9be43-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="9be43-107">Aby umieścić znaki cudzysłowu w ciągu w kodzie</span><span class="sxs-lookup"><span data-stu-id="9be43-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="9be43-108">W [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], Wstaw dwa znaki cudzysłowu w wierszu jako osadzony znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="9be43-108">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="9be43-109">W [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Wstaw sekwencji unikowej \\"jako osadzony znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="9be43-109">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="9be43-110">Na przykład aby utworzyć parametry poprzedniego, należy użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="9be43-110">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="9be43-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="9be43-111">-or-</span></span>  
  
2.  <span data-ttu-id="9be43-112">Wstaw znak ASCII lub Unicode dla znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="9be43-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="9be43-113">W [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], użyj znaków ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="9be43-113">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], use the ASCII character (34).</span></span> <span data-ttu-id="9be43-114">W [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], użyj znaku Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="9be43-114">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9be43-115">W tym przykładzie można użyć \u0022, ponieważ nie można użyć nazwa zawierająca znaki uniwersalne określający znaku w podstawowym zestawie znaków.</span><span class="sxs-lookup"><span data-stu-id="9be43-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="9be43-116">W przeciwnym razie należy utworzyć C3851.</span><span class="sxs-lookup"><span data-stu-id="9be43-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="9be43-117">Aby uzyskać więcej informacji, zobacz [C3851 błąd kompilatora](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="9be43-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="9be43-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="9be43-118">-or-</span></span>  
  
3.  <span data-ttu-id="9be43-119">Można również zdefiniować stałą znaku i użyć go w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="9be43-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9be43-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9be43-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="9be43-121">Informacje o formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="9be43-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="9be43-122">Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9be43-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="9be43-123">Porady: Tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9be43-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="9be43-124">Porady: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9be43-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="9be43-125">Porady: Zaznaczanie tekstu w oknach formantu TextBox formularzy</span><span class="sxs-lookup"><span data-stu-id="9be43-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="9be43-126">Porady: wyświetlanie wielu wierszy w oknach formantu TextBox formularzy</span><span class="sxs-lookup"><span data-stu-id="9be43-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="9be43-127">TextBox — formant</span><span class="sxs-lookup"><span data-stu-id="9be43-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
