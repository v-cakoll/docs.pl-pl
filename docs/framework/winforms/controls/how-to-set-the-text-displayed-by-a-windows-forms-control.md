---
title: Ustawianie tekstu wyświetlanego przez kontrolkę
description: Dowiedz się, jak ustawić tekst wyświetlany przez kontrolkę Windows Forms. Ustaw lub Zwróć tekst przy użyciu właściwości text lub zmień czcionkę przy użyciu właściwości font.
ms.date: 08/20/2019
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
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622851"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="cd9a3-104">Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd9a3-104">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="cd9a3-105">Kontrolki Windows Forms zwykle wyświetlają tekst, który jest powiązany z podstawową funkcją formantu.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-105">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="cd9a3-106">Na przykład <xref:System.Windows.Forms.Button> kontrolka zazwyczaj wyświetla podpis wskazujący, jaka akcja zostanie wykonana po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-106">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="cd9a3-107">Dla wszystkich kontrolek można ustawić lub zwrócić tekst przy użyciu <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-107">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="cd9a3-108">Można zmienić czcionkę przy użyciu <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-108">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="cd9a3-109">Możesz również ustawić tekst za pomocą [projektanta](#designer).</span><span class="sxs-lookup"><span data-stu-id="cd9a3-109">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="cd9a3-110">Programowa</span><span class="sxs-lookup"><span data-stu-id="cd9a3-110">Programmatic</span></span>

1. <span data-ttu-id="cd9a3-111">Ustaw <xref:System.Windows.Forms.Control.Text%2A> Właściwość na ciąg.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="cd9a3-112">Aby utworzyć podkreślony klucz dostępu, program zawiera znak handlowego "i" (&) przed literą, która będzie kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-112">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="cd9a3-113">Ustaw <xref:System.Windows.Forms.Control.Font%2A> Właściwość na obiekt typu <xref:System.Drawing.Font> .</span><span class="sxs-lookup"><span data-stu-id="cd9a3-113">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > <span data-ttu-id="cd9a3-114">Możesz użyć znaku ucieczki, aby wyświetlić specjalny znak w elementach interfejsu użytkownika, które zwykle interpretują je inaczej, takich jak elementy menu.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-114">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="cd9a3-115">Na przykład poniższy wiersz kodu ustawia tekst elementu menu do odczytania "& teraz dla czegoś zupełnie innego":</span><span class="sxs-lookup"><span data-stu-id="cd9a3-115">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="cd9a3-116">Projektant</span><span class="sxs-lookup"><span data-stu-id="cd9a3-116">Designer</span></span>

1. <span data-ttu-id="cd9a3-117">W oknie **Właściwości** w programie Visual Studio ustaw właściwość **Text** kontrolki na odpowiedni ciąg.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-117">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="cd9a3-118">Aby utworzyć podkreślony klawisz skrótu, program zawiera znak handlowego "i" (&) przed literą, która będzie klawiszem skrótu.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-118">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="cd9a3-119">W oknie **Właściwości** wybierz przycisk wielokropka ( ![ przycisk wielokropka (...) w okno właściwości programu Visual Studio ](./media/visual-studio-ellipsis-button.png) ) obok właściwości **Font** .</span><span class="sxs-lookup"><span data-stu-id="cd9a3-119">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="cd9a3-120">W oknie dialogowym Czcionka standardowa wybierz czcionkę, styl czcionki, rozmiar, efekty (na przykład przekreślenie lub podkreślenie) i skrypt, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-120">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd9a3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd9a3-121">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cd9a3-122">Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd9a3-122">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="cd9a3-123">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd9a3-123">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
