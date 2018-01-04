---
title: "Porady: tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows"
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
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fe8c3c6ac3c0f47f5e78aa7ff3242a0c69c7f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="c1df6-102">Porady: tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c1df6-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="c1df6-103">Pole hasła jest pole tekstowe formularzy systemu Windows, które wyświetla symboli zastępczych, gdy użytkownik wpisuje ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="c1df6-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="c1df6-104">Aby utworzyć pole tekstowe hasła</span><span class="sxs-lookup"><span data-stu-id="c1df6-104">To create a password text box</span></span>  
  
1.  <span data-ttu-id="c1df6-105">Ustaw <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwość <xref:System.Windows.Forms.TextBox> formantu do określonego znaku.</span><span class="sxs-lookup"><span data-stu-id="c1df6-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="c1df6-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Właściwość określa znak wyświetlany w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="c1df6-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="c1df6-107">Na przykład gwiazdki wyświetlana w polu hasła, określ * dla <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="c1df6-107">For example, if you want asterisks displayed in the password box, specify * for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="c1df6-108">Następnie niezależnie od tego, jakie użytkownik wpisze w polu tekstowym znak, wyświetlana jest gwiazdka.</span><span class="sxs-lookup"><span data-stu-id="c1df6-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2.  <span data-ttu-id="c1df6-109">(Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c1df6-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="c1df6-110">Właściwość określa, ile znaków można wpisać w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="c1df6-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="c1df6-111">Po przekroczeniu maksymalnego system emituje sygnał dźwiękowy i pole tekstowe nie akceptuje żadnych więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="c1df6-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="c1df6-112">Należy pamiętać, że nie możesz w tym celu jako maksymalną długość hasła może być używany do hakerami próbuje odgadnąć hasło.</span><span class="sxs-lookup"><span data-stu-id="c1df6-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="c1df6-113">Poniższy przykład kodu pokazuje, jak zainicjować pole tekstowe, które będzie akceptować ciąg do 14 znaków i wyświetlić gwiazdki zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="c1df6-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="c1df6-114">`InitializeMyControl` Procedury nie będą automatycznie wykonywane; musi zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="c1df6-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c1df6-115">Przy użyciu <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości pola tekstowego pozwala zagwarantować, inne osoby nie będą mogli określić hasło użytkownika, jeśli one przestrzegać użytkownika, wprowadzając ją.</span><span class="sxs-lookup"><span data-stu-id="c1df6-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="c1df6-116">To zabezpieczenie nie obejmuje dowolny rodzaj gromadzenia i przekazywania hasła, które może wystąpić z powodu logiki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1df6-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="c1df6-117">Ponieważ wprowadzony tekst nie są szyfrowane w dowolny sposób, należy traktować jak w przypadku innych poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="c1df6-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="c1df6-118">Mimo że nie ma tak, hasło nadal jest traktowana jako zwykły tekst (chyba że zaimplementowano pewne dodatkowe zabezpieczenie).</span><span class="sxs-lookup"><span data-stu-id="c1df6-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c1df6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1df6-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="c1df6-120">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c1df6-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="c1df6-121">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1df6-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c1df6-122">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c1df6-122">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="c1df6-123">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="c1df6-123">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="c1df6-124">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1df6-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c1df6-125">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1df6-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c1df6-126">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c1df6-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
