---
title: 'Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 56391777c75db288c33d1b2192355be0df50f7ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046120"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="3e819-102">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3e819-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="3e819-103">Pole hasła to Windows Forms pole tekstowe, które wyświetla znaki zastępcze, gdy użytkownik wpisze ciąg.</span><span class="sxs-lookup"><span data-stu-id="3e819-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="3e819-104">Aby utworzyć pole tekstowe hasła</span><span class="sxs-lookup"><span data-stu-id="3e819-104">To create a password text box</span></span>

1. <span data-ttu-id="3e819-105"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Ustaw właściwość <xref:System.Windows.Forms.TextBox> kontrolki na określony znak.</span><span class="sxs-lookup"><span data-stu-id="3e819-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="3e819-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Właściwość określa znak wyświetlany w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="3e819-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="3e819-107">Na przykład, jeśli chcesz, aby gwiazdki były wyświetlane w polu hasło, określ \* dla <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości w okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e819-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="3e819-108">Następnie, niezależnie od tego, jaki znak jest wpisany przez użytkownika w polu tekstowym, zostanie wyświetlona gwiazdka.</span><span class="sxs-lookup"><span data-stu-id="3e819-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="3e819-109">Obowiązkowe <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> Ustaw właściwość.</span><span class="sxs-lookup"><span data-stu-id="3e819-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="3e819-110">Właściwość określa liczbę znaków, które można wpisać w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="3e819-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="3e819-111">W przypadku przekroczenia maksymalnej długości system emituje sygnał dźwiękowy, a pole tekstowe nie akceptuje więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="3e819-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="3e819-112">Zwróć uwagę, że nie chcesz tego robić, ponieważ maksymalna długość hasła może być używana przez hakerów próbujących złamać hasło.</span><span class="sxs-lookup"><span data-stu-id="3e819-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="3e819-113">Poniższy przykład kodu pokazuje, jak zainicjować pole tekstowe, które akceptuje ciąg o długości do 14 znaków i wyświetla gwiazdki zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="3e819-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="3e819-114">`InitializeMyControl` Procedura nie zostanie wykonana automatycznie; musi być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3e819-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3e819-115"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Użycie właściwości w polu tekstowym może pomóc w zapewnieniu, że inne osoby nie będą mogły określić hasła użytkownika, jeśli zaobserwują użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3e819-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="3e819-116">Ta miara zabezpieczeń nie obejmuje żadnego rodzaju magazynu ani przesyłania hasła, które może wystąpić z powodu logiki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e819-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="3e819-117">Ponieważ wprowadzony tekst nie jest w żaden sposób szyfrowany, należy go traktować tak jak wszystkie inne poufne dane.</span><span class="sxs-lookup"><span data-stu-id="3e819-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="3e819-118">Mimo że nie jest on wyświetlany jako taki, hasło jest nadal traktowane jako ciąg tekstowy (chyba że zaimplementowano dodatkową miarę zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="3e819-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3e819-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e819-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="3e819-120">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="3e819-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="3e819-121">Instrukcje: Kontrolowanie punktu wstawiania w kontrolce TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e819-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="3e819-122">Instrukcje: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3e819-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="3e819-123">Instrukcje: Umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="3e819-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="3e819-124">Instrukcje: Zaznacz tekst w kontrolce TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e819-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="3e819-125">Instrukcje: Wyświetl wiele wierszy w kontrolce TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e819-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="3e819-126">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3e819-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
