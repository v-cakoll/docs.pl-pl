---
title: "Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows"
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a81c2202400968b4d4c95b40de7476fbd68d6182
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="8cf55-102">Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8cf55-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="8cf55-103">Formanty formularzy systemu Windows zazwyczaj wyświetlić tekst związany z podstawowej funkcji formantu.</span><span class="sxs-lookup"><span data-stu-id="8cf55-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="8cf55-104">Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle zawiera nagłówek wskazującą, jakie działania zostaną wykonane, po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="8cf55-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="8cf55-105">Dla wszystkich kontrolek, można ustawić lub zwróć tekst za pomocą <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cf55-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="8cf55-106">Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cf55-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="8cf55-107">Można również ustawić tekst przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="8cf55-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="8cf55-108">Zobacz też [jak: utworzyć dostępu do kluczy dla systemu Windows formularzy formantów przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [porady: ustawić tekst wyświetlany za pomocą formantu formularzy systemu Windows projektanta](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [porady: Ustawianie obrazu Wyświetlany przez formant przy użyciu narzędzia Projektant formularzy systemu Windows](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8cf55-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="8cf55-109">Aby ustawić tekst wyświetlany przez formant programowo</span><span class="sxs-lookup"><span data-stu-id="8cf55-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="8cf55-110">Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości na ciąg.</span><span class="sxs-lookup"><span data-stu-id="8cf55-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="8cf55-111">Można utworzyć klucza dostępu podkreślony obejmuje handlowego "i" (&) przed literą, która będzie klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="8cf55-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="8cf55-112">Ustaw <xref:System.Windows.Forms.Control.Font%2A> dla właściwości typu obiektu <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="8cf55-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
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
    >  <span data-ttu-id="8cf55-113">Znak ucieczki służy do wyświetlania znaków specjalnych w elementy interfejsu użytkownika, które będzie zwykle je interpretować, takich jak elementy menu.</span><span class="sxs-lookup"><span data-stu-id="8cf55-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="8cf55-114">Na przykład następujący wiersz kodu ustawia tekst elementu menu do odczytu "& teraz na coś dwóch zupełnie różnych":</span><span class="sxs-lookup"><span data-stu-id="8cf55-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8cf55-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cf55-115">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8cf55-116">Porady: Tworzenie klawiszy dostępu dla formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8cf55-116">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [<span data-ttu-id="8cf55-117">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8cf55-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
