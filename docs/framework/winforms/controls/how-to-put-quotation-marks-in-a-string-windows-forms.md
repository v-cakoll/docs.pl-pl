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
ms.workload: dotnet
ms.openlocfilehash: 267a69b9470040dfc60f3c0b280b71e3f52dbc88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="804a1-102">Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="804a1-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="804a1-103">Czasami może chcesz umieścić znaki cudzysłowu ("") w ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="804a1-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="804a1-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="804a1-104">For example:</span></span>  
  
 <span data-ttu-id="804a1-105">Użytkownik nazywany "Wymagają Traktuj!"</span><span class="sxs-lookup"><span data-stu-id="804a1-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="804a1-106">Alternatywnie, można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako stała.</span><span class="sxs-lookup"><span data-stu-id="804a1-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="804a1-107">Aby umieścić znaki cudzysłowu w ciągu w kodzie</span><span class="sxs-lookup"><span data-stu-id="804a1-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="804a1-108">W [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], Wstaw dwa znaki cudzysłowu w wierszu jako osadzony znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="804a1-108">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="804a1-109">W [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Wstaw sekwencji unikowej \\"jako osadzony znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="804a1-109">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="804a1-110">Na przykład aby utworzyć parametry poprzedniego, należy użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="804a1-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="804a1-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="804a1-111">-or-</span></span>  
  
2.  <span data-ttu-id="804a1-112">Wstaw znak ASCII lub Unicode dla znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="804a1-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="804a1-113">W [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], użyj znaków ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="804a1-113">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], use the ASCII character (34).</span></span> <span data-ttu-id="804a1-114">W [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], użyj znaku Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="804a1-114">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], use the Unicode character (\u0022).</span></span>  
  
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
    >  <span data-ttu-id="804a1-115">W tym przykładzie można użyć \u0022, ponieważ nie można użyć nazwa zawierająca znaki uniwersalne określający znaku w podstawowym zestawie znaków.</span><span class="sxs-lookup"><span data-stu-id="804a1-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="804a1-116">W przeciwnym razie należy utworzyć C3851.</span><span class="sxs-lookup"><span data-stu-id="804a1-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="804a1-117">Aby uzyskać więcej informacji, zobacz [C3851 błąd kompilatora](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="804a1-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="804a1-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="804a1-118">-or-</span></span>  
  
3.  <span data-ttu-id="804a1-119">Można również zdefiniować stałą znaku i użyć go w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="804a1-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="804a1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="804a1-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="804a1-121">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="804a1-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="804a1-122">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="804a1-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="804a1-123">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="804a1-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="804a1-124">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="804a1-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="804a1-125">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="804a1-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="804a1-126">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="804a1-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="804a1-127">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="804a1-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
