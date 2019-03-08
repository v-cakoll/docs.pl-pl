---
title: 'Instrukcje: Zmienianie stylu elementu w modelu obiektów zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: ad91f7591e2fa07605fe4f7ac026b7c969ab7ef0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678940"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="66709-102">Instrukcje: Zmienianie stylu elementu w modelu obiektów zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="66709-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>

<span data-ttu-id="66709-103">Aby sterować wyglądem dokumentu i jej elementów, można użyć style w formacie HTML.</span><span class="sxs-lookup"><span data-stu-id="66709-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="66709-104"><xref:System.Windows.Forms.HtmlDocument> i <xref:System.Windows.Forms.HtmlElement> obsługuje <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwości, które pobierają ciągi stylu następujący format:</span><span class="sxs-lookup"><span data-stu-id="66709-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>

`name1:value1;...;nameN:valueN;`

<span data-ttu-id="66709-105">Oto `DIV` ciągiem styl, który ustawia czcionka Arial i cały tekst pogrubiony:</span><span class="sxs-lookup"><span data-stu-id="66709-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

<span data-ttu-id="66709-106">Problem dotyczący manipulowanie stylów za pomocą <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwość jest, że można potwierdzić kłopotliwe dodać do, a następnie usuń ustawienia stylu pracy z ciągu.</span><span class="sxs-lookup"><span data-stu-id="66709-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="66709-107">Na przykład stałyby złożonych procedurę renderowania poprzedni tekst kursywą zawsze wtedy, gdy użytkownik umieszcza kursor nad `DIV`i kursywa wyłączone, gdy kursor opuszcza `DIV`.</span><span class="sxs-lookup"><span data-stu-id="66709-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="66709-108">Czas może stać się problemem, jeśli zachodzi potrzeba manipulowania dużej liczby style w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="66709-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>

<span data-ttu-id="66709-109">Poniższa procedura zawiera kod, który umożliwia łatwe manipulowanie stylów, dokumenty HTML i elementów.</span><span class="sxs-lookup"><span data-stu-id="66709-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="66709-110">Procedura wymaga, że wiesz, jak wykonać podstawowe zadania w Windows Forms, takie jak tworzenie nowego projektu i dodawanie formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="66709-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>

### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="66709-111">Aby przetworzyć zmiany stylów w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66709-111">To process style changes in a Windows Forms application</span></span>

1. <span data-ttu-id="66709-112">Utwórz nowy projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="66709-112">Create a new Windows Forms project.</span></span>

2. <span data-ttu-id="66709-113">Utwórz nowy plik klasy kończące się na rozszerzenie, które są odpowiednie dla języka programowania.</span><span class="sxs-lookup"><span data-stu-id="66709-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>

3. <span data-ttu-id="66709-114">Kopiuj `StyleGenerator` klasy kod w sekcji przykład tego tematu w pliku klasy, a następnie zapisz kod.</span><span class="sxs-lookup"><span data-stu-id="66709-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>

4. <span data-ttu-id="66709-115">Zapisz poniższy kod HTML w pliku o nazwie Test.htm.</span><span class="sxs-lookup"><span data-stu-id="66709-115">Save the following HTML to a file named Test.htm.</span></span>

    ```html
    <HTML>
        <BODY>

            <DIV style="font-face:arial;font-weight:bold;">
                Hello, world!
            </DIV><P>

            <DIV>
                Hello again, world!
            </DIV><P>

        </BODY>
    </HTML>
    ```

5. <span data-ttu-id="66709-116">Dodaj <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1` do formularza głównego projektu.</span><span class="sxs-lookup"><span data-stu-id="66709-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>

6. <span data-ttu-id="66709-117">Dodaj następujący kod do pliku kodu projektu.</span><span class="sxs-lookup"><span data-stu-id="66709-117">Add the following code to your project's code file.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="66709-118">Upewnij się, że `webBrowser1_DocumentCompleted` programu obsługi zdarzeń jest skonfigurowany jako odbiornika dla <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="66709-118">Ensure that the `webBrowser1_DocumentCompleted` event handler is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="66709-119">W programie Visual Studio, kliknij dwukrotnie <xref:System.Windows.Forms.WebBrowser> formant; w edytorze tekstów, skonfiguruj odbiornik programowo.</span><span class="sxs-lookup"><span data-stu-id="66709-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>

    [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
    [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]

7. <span data-ttu-id="66709-120">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="66709-120">Run the project.</span></span> <span data-ttu-id="66709-121">Uruchom kursor nad pierwszym `DIV` aby obserwować wyniki kodu.</span><span class="sxs-lookup"><span data-stu-id="66709-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>

## <a name="example"></a><span data-ttu-id="66709-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="66709-122">Example</span></span>

<span data-ttu-id="66709-123">Poniższy przykład kodu pokazuje pełny kod `StyleGenerator` klasy, która analizuje istniejącą wartość stylu, obsługuje dodawanie, zmienianie i usuwanie stylów i zwraca nową wartość stylu z żądanych zmian.</span><span class="sxs-lookup"><span data-stu-id="66709-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>

[!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
[!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]

## <a name="see-also"></a><span data-ttu-id="66709-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66709-124">See also</span></span>

- <xref:System.Windows.Forms.HtmlElement>
