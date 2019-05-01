---
title: 'Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 59570af89e6236e3c13866d45dc5361d52b84274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013091"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="7e856-102">Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7e856-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="7e856-103">Kontrolek formularzy Windows Forms jest zazwyczaj wyświetlane jakiś tekst, który jest powiązany z podstawową funkcją kontroli.</span><span class="sxs-lookup"><span data-stu-id="7e856-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="7e856-104">Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle zawiera nagłówek wskazującą, jakie działania będą wykonywane po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="7e856-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="7e856-105">Dla wszystkich kontrolek, możesz ustawić lub zwróć tekst przy użyciu <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e856-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="7e856-106">Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e856-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="7e856-107">Można również ustawić tekst za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="7e856-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="7e856-108">Zobacz też [jak: Tworzenie klawiszy dostępu dla Windows Forms przy użyciu narzędzia Projektant formantów](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [jak: Ustawianie tekstu wyświetlanego przez Windows Forms przy użyciu narzędzia Projektant](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [jak: Ustawianie obrazu wyświetlanego przez Windows Forms przy użyciu narzędzia Projektant](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7e856-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="7e856-109">Aby ustawić tekst wyświetlany przez kontrolkę programowe</span><span class="sxs-lookup"><span data-stu-id="7e856-109">To set the text displayed by a control programmatically</span></span>  
  
1. <span data-ttu-id="7e856-110">Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości na ciąg.</span><span class="sxs-lookup"><span data-stu-id="7e856-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="7e856-111">Aby utworzyć klucz dostępu podkreślony obejmuje handlowe "i" (&) przed literą, która będzie klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="7e856-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2. <span data-ttu-id="7e856-112">Ustaw <xref:System.Windows.Forms.Control.Font%2A> właściwość do obiektu typu <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="7e856-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7e856-113">Aby wyświetlić znaki specjalne w elementach interfejsu użytkownika, które będą zwykle je interpretować, takich jak elementy menu, można użyć znaku ucieczki.</span><span class="sxs-lookup"><span data-stu-id="7e856-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="7e856-114">Na przykład, następujący wiersz kodu ustawia element menu tekstu do odczytania "& teraz do czegoś zupełnie inny":</span><span class="sxs-lookup"><span data-stu-id="7e856-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7e856-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e856-115">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7e856-116">Instrukcje: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e856-116">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="7e856-117">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="7e856-117">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
