---
title: 'Porady: umieszczanie cudzysłowu w ciągu'
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
ms.openlocfilehash: c14747291d6c41144eef97b258f852bbe14ef07d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735901"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="aa68d-102">Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="aa68d-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="aa68d-103">Czasami warto umieścić znaki cudzysłowu ("") w ciągu tekstu.</span><span class="sxs-lookup"><span data-stu-id="aa68d-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="aa68d-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="aa68d-104">For example:</span></span>  
  
 <span data-ttu-id="aa68d-105">"Nie zawarto".</span><span class="sxs-lookup"><span data-stu-id="aa68d-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="aa68d-106">Alternatywnie można również użyć pola <xref:Microsoft.VisualBasic.ControlChars.Quote> jako stałej.</span><span class="sxs-lookup"><span data-stu-id="aa68d-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="aa68d-107">Aby umieścić znaki cudzysłowu w ciągu w kodzie</span><span class="sxs-lookup"><span data-stu-id="aa68d-107">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="aa68d-108">W Visual Basic Wstaw dwa cudzysłowy w wierszu jako osadzony znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="aa68d-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="aa68d-109">W wizualizacjach C# i C++wizualizacji Wstaw sekwencję ucieczki \\"jako osadzony cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="aa68d-109">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="aa68d-110">Na przykład, aby utworzyć poprzedni ciąg, użyj poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="aa68d-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="aa68d-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="aa68d-111">-or-</span></span>  
  
2. <span data-ttu-id="aa68d-112">Wstaw znak ASCII lub Unicode dla znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="aa68d-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="aa68d-113">W Visual Basic Użyj znaku ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="aa68d-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="aa68d-114">W wizualizacji C#Użyj znaku Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="aa68d-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    > <span data-ttu-id="aa68d-115">W tym przykładzie nie można użyć \u0022, ponieważ nie można użyć uniwersalnej nazwy znaku, która określa znak w podstawowym zestawie znaków.</span><span class="sxs-lookup"><span data-stu-id="aa68d-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="aa68d-116">W przeciwnym razie utworzysz C3851.</span><span class="sxs-lookup"><span data-stu-id="aa68d-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="aa68d-117">Aby uzyskać więcej informacji, zobacz [błąd kompilatora C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="aa68d-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="aa68d-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="aa68d-118">-or-</span></span>  
  
3. <span data-ttu-id="aa68d-119">Możesz również zdefiniować stałą dla znaku i użyć go w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="aa68d-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa68d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa68d-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="aa68d-121">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="aa68d-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="aa68d-122">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa68d-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="aa68d-123">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa68d-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="aa68d-124">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aa68d-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="aa68d-125">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa68d-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="aa68d-126">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa68d-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="aa68d-127">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="aa68d-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
