---
title: 'Porady: zmienianie stylu elementu w modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e833a15e33d0baf80f0078b26758137e7908a8fd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="e921d-102">Porady: zmienianie stylu elementu w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="e921d-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="e921d-103">Aby sterować wyglądem dokumentu i jego elementów, można użyć style w formacie HTML.</span><span class="sxs-lookup"><span data-stu-id="e921d-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="e921d-104"><xref:System.Windows.Forms.HtmlDocument> i <xref:System.Windows.Forms.HtmlElement> obsługuje <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwości, które pobierają ciągi styl następujący format:</span><span class="sxs-lookup"><span data-stu-id="e921d-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="e921d-105">Oto `DIV` ciągiem styl, który ustawia czcionkę Arial i cały tekst, które mają zostać pogrubione:</span><span class="sxs-lookup"><span data-stu-id="e921d-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="e921d-106">Problem z manipulowanie stylów za pomocą <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwość jest, że może okazać skomplikowane, aby dodać do, a następnie usuń ustawień stylu z ciągu.</span><span class="sxs-lookup"><span data-stu-id="e921d-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="e921d-107">Na przykład go staje się złożona procedura umożliwiające renderowanie poprzedniego tekstu kursywą zawsze, gdy użytkownik umieszcza kursor nad `DIV`i podjąć kursywa poza gdy kursor opuszcza `DIV`.</span><span class="sxs-lookup"><span data-stu-id="e921d-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="e921d-108">Czas może stać się problemem, jeśli potrzebujesz do manipulowania dużą liczbę style w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="e921d-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="e921d-109">Poniższa procedura zawiera kod, który umożliwia łatwe manipulowania style dla dokumentów HTML i elementów.</span><span class="sxs-lookup"><span data-stu-id="e921d-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="e921d-110">Procedura wymaga się, że wiesz, jak wykonać podstawowe zadania w formularzach systemu Windows, takie jak tworzenie nowego projektu i dodawanie formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="e921d-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="e921d-111">Aby przetwarzać zmiany stylu w aplikacji formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e921d-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="e921d-112">Utwórz nowy projekt formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e921d-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="e921d-113">Utwórz nowy plik klasy końcowy w rozszerzeniu właściwe dla języka programowania.</span><span class="sxs-lookup"><span data-stu-id="e921d-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="e921d-114">Kopiuj `StyleGenerator` klasy kodu w przykładzie sekcji tego tematu w pliku klasy, a następnie zapisz kod.</span><span class="sxs-lookup"><span data-stu-id="e921d-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="e921d-115">Zapisz plik o nazwie Test.htm poniższy kod HTML.</span><span class="sxs-lookup"><span data-stu-id="e921d-115">Save the following HTML to a file named Test.htm.</span></span>  
  
    ```  
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
  
5.  <span data-ttu-id="e921d-116">Dodaj <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1` w formularzu głównym projektu.</span><span class="sxs-lookup"><span data-stu-id="e921d-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="e921d-117">Dodaj następujący kod do pliku kodu projektu.</span><span class="sxs-lookup"><span data-stu-id="e921d-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e921d-118">Upewnij się, że `webBrowser1_DocumentCompleted` programu obsługi zdarzeń jest skonfigurowany jako odbiornika dla <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e921d-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="e921d-119">W programie Visual Studio, kliknij dwukrotnie <xref:System.Windows.Forms.WebBrowser> kontrolować; w edytorze tekstów, skonfiguruj odbiornik programowo.</span><span class="sxs-lookup"><span data-stu-id="e921d-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="e921d-120">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="e921d-120">Run the project.</span></span> <span data-ttu-id="e921d-121">Uruchom kursor nad pierwszy `DIV` obserwować efekty kodu.</span><span class="sxs-lookup"><span data-stu-id="e921d-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e921d-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e921d-122">Example</span></span>  
 <span data-ttu-id="e921d-123">Poniższy przykładowy kod przedstawia pełny kod `StyleGenerator` obsługuje klasy, która analizuje istniejącej wartości stylu, dodawanie, zmienianie i usuwanie style i zwraca nową wartość stylu z żądanych zmian.</span><span class="sxs-lookup"><span data-stu-id="e921d-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e921d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e921d-124">See Also</span></span>  
 <xref:System.Windows.Forms.HtmlElement>
