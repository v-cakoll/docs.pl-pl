---
title: 'Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 7fcc2e8692880f1e5c2b8df807cf7943a5575c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534836"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="c85a2-102">Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="c85a2-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="c85a2-103">Czasami może chcesz umieścić znaki cudzysłowu ("") w ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="c85a2-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="c85a2-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c85a2-104">For example:</span></span>  
  
 <span data-ttu-id="c85a2-105">Użytkownik nazywany "Wymagają Traktuj!"</span><span class="sxs-lookup"><span data-stu-id="c85a2-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="c85a2-106">Alternatywnie, można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako stała.</span><span class="sxs-lookup"><span data-stu-id="c85a2-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="c85a2-107">Aby umieścić znaki cudzysłowu w ciągu w kodzie</span><span class="sxs-lookup"><span data-stu-id="c85a2-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="c85a2-108">W języku Visual Basic Wstaw dwa znaki cudzysłowu w wierszu jako osadzony znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="c85a2-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="c85a2-109">W środowisku Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Wstaw sekwencji unikowej \\"jako osadzony znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="c85a2-109">In Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="c85a2-110">Na przykład aby utworzyć parametry poprzedniego, należy użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="c85a2-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="c85a2-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="c85a2-111">-or-</span></span>  
  
2.  <span data-ttu-id="c85a2-112">Wstaw znak ASCII lub Unicode dla znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="c85a2-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="c85a2-113">W języku Visual Basic użyj znaków ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="c85a2-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="c85a2-114">W środowisku Visual C#, użyj znaków Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="c85a2-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    >  <span data-ttu-id="c85a2-115">W tym przykładzie można użyć \u0022, ponieważ nie można użyć nazwa zawierająca znaki uniwersalne określający znaku w podstawowym zestawie znaków.</span><span class="sxs-lookup"><span data-stu-id="c85a2-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="c85a2-116">W przeciwnym razie należy utworzyć C3851.</span><span class="sxs-lookup"><span data-stu-id="c85a2-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="c85a2-117">Aby uzyskać więcej informacji, zobacz [C3851 błąd kompilatora](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="c85a2-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="c85a2-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="c85a2-118">-or-</span></span>  
  
3.  <span data-ttu-id="c85a2-119">Można również zdefiniować stałą znaku i użyć go w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="c85a2-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c85a2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c85a2-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="c85a2-121">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c85a2-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="c85a2-122">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c85a2-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c85a2-123">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c85a2-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c85a2-124">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c85a2-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="c85a2-125">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c85a2-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c85a2-126">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c85a2-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c85a2-127">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c85a2-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
