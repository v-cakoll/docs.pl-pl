---
title: 'Instrukcje: Umieszczanie cudzysłowu w ciągu (Windows Forms)'
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
ms.openlocfilehash: 24d7ea17384a912fda454bfb1136696ab18d9843
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651646"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="575de-102">Instrukcje: Umieszczanie cudzysłowu w ciągu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="575de-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="575de-103">Czasami możesz chcieć umieścić znaki cudzysłowu ("") w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="575de-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="575de-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="575de-104">For example:</span></span>  
  
 <span data-ttu-id="575de-105">Ona twierdzi "Oferującego Traktuj!"</span><span class="sxs-lookup"><span data-stu-id="575de-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="575de-106">Alternatywnie, można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pola jako stała.</span><span class="sxs-lookup"><span data-stu-id="575de-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="575de-107">Aby umieścić znaki cudzysłowu w ciągu w kodzie</span><span class="sxs-lookup"><span data-stu-id="575de-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="575de-108">W języku Visual Basic należy wstawić dwa znaki cudzysłowu w wierszu jako osadzonego znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="575de-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="575de-109">W elemencie wizualnym C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Wstaw sekwencja unikowa \\"jako osadzonego znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="575de-109">In Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="575de-110">Na przykład utworzyć poprzedniego parametry, należy użyć następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="575de-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="575de-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="575de-111">-or-</span></span>  
  
2.  <span data-ttu-id="575de-112">Wstaw znak ASCII lub Unicode dla znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="575de-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="575de-113">W języku Visual Basic należy użyć znaku ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="575de-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="575de-114">W elemencie wizualnym C#, należy użyć znaku Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="575de-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    >  <span data-ttu-id="575de-115">W tym przykładzie nie można użyć \u0022, ponieważ nie można użyć nazwy znaki uniwersalne, opisująca do znaku w podstawowym zestawie znaków.</span><span class="sxs-lookup"><span data-stu-id="575de-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="575de-116">W przeciwnym razie zostanie wyświetlony C3851.</span><span class="sxs-lookup"><span data-stu-id="575de-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="575de-117">Aby uzyskać więcej informacji, zobacz [błąd kompilatora C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="575de-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="575de-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="575de-118">-or-</span></span>  
  
3.  <span data-ttu-id="575de-119">Można również zdefiniować stałą znaku i używać jej w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="575de-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="575de-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="575de-120">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="575de-121">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="575de-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="575de-122">Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="575de-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="575de-123">Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="575de-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="575de-124">Instrukcje: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="575de-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="575de-125">Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="575de-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="575de-126">Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="575de-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="575de-127">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="575de-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
