---
title: "Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19c47c21526ca6e7aa4046a1853f3d1743438d17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="cc23e-102">Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="cc23e-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="cc23e-103">*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykiety formantu, takie jak przycisk.</span><span class="sxs-lookup"><span data-stu-id="cc23e-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="cc23e-104">Umożliwia użytkownikowi "przycisk" naciśnięcie klawisza ALT w połączeniu z kluczem dostępu wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="cc23e-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="cc23e-105">Na przykład, gdy przycisk działa procedura Drukowanie formularza i dlatego jego `Text` właściwość ma wartość "Print" Dodawanie ampersand (&) przed literą "P" powoduje, że litery "P", aby podkreślić tekst przycisku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cc23e-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="cc23e-106">Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P.</span><span class="sxs-lookup"><span data-stu-id="cc23e-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="cc23e-107">Nie może mieć klucza dostępu dla formantu, który nie może uzyskać fokusu.</span><span class="sxs-lookup"><span data-stu-id="cc23e-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc23e-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="cc23e-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cc23e-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="cc23e-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cc23e-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cc23e-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="cc23e-111">Aby utworzyć klucz dostępu dla formantu</span><span class="sxs-lookup"><span data-stu-id="cc23e-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="cc23e-112">W **właściwości** ustaw `Text` właściwości ciąg, który zawiera handlowego "i" (&) przed literą, która będzie klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="cc23e-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="cc23e-113">Na przykład aby ustawić literę "P" jako klawisz dostępu, wpisz **& Drukuj** w siatce.</span><span class="sxs-lookup"><span data-stu-id="cc23e-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc23e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc23e-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="cc23e-115">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc23e-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="cc23e-116">Porady: Ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc23e-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="cc23e-117">Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="cc23e-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
