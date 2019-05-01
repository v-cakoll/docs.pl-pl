---
title: 'Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML a kodem aplikacji klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: cf1391e88c03095e0851d75ae6d50f8e809d13e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797192"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="84e8a-102">Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML a kodem aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="84e8a-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="84e8a-103">Możesz użyć <xref:System.Windows.Forms.WebBrowser> formantu, aby dodać istniejący dynamiczny kod aplikacji sieci Web HTML (DHTML) do aplikacji klienta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84e8a-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="84e8a-104">Jest to przydatne, gdy zainwestowali czas opracowywania znaczące w tworzeniu kontrolek na podstawie DHTML i chcesz korzystać z zalet użytkownikowi możliwości interfejsu Windows Forms bez konieczności ponownego zapisania istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="84e8a-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="84e8a-105"><xref:System.Windows.Forms.WebBrowser> Kontrola umożliwia Implementowanie dwukierunkowej komunikacji między kodu aplikacji klienckich i skryptów kodu strony sieci Web za pomocą <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> i <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="84e8a-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="84e8a-106">Ponadto można skonfigurować <xref:System.Windows.Forms.WebBrowser> kontrolki formantów sieci Web programu blend bezproblemowo z innymi formantami na formularzu aplikacji ukrywanie ich implementacji DHTML.</span><span class="sxs-lookup"><span data-stu-id="84e8a-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="84e8a-107">Aby dopasować bezproblemowo formanty, formatowanie stronę wyświetlaną, aby jej kolor tła i stylu wizualnego dopasowania pozostałej części formularza i używać <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, i <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości, aby wyłączyć funkcje standardową przeglądarką.</span><span class="sxs-lookup"><span data-stu-id="84e8a-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="84e8a-108">Aby osadzić DHTML w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84e8a-108">To embed DHTML in your Windows Forms application</span></span>  
  
1. <span data-ttu-id="84e8a-109">Ustaw <xref:System.Windows.Forms.WebBrowser> kontrolki <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` aby zapobiec <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików upuszczone na go.</span><span class="sxs-lookup"><span data-stu-id="84e8a-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2. <span data-ttu-id="84e8a-110">Ustaw dla formantu <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlanie jego menu skrótów, gdy użytkownik kliknie prawym przyciskiem myszy go.</span><span class="sxs-lookup"><span data-stu-id="84e8a-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3. <span data-ttu-id="84e8a-111">Ustaw dla formantu <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli ją klawiszy skrótów.</span><span class="sxs-lookup"><span data-stu-id="84e8a-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4. <span data-ttu-id="84e8a-112">Ustaw <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> właściwość w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="84e8a-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="84e8a-113">W poniższym kodzie użyto samej klasy formularza dla skryptów obiektu.</span><span class="sxs-lookup"><span data-stu-id="84e8a-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="84e8a-114">Component Object Model (COM) musi mieć możliwość dostępu do obiektu skryptów.</span><span class="sxs-lookup"><span data-stu-id="84e8a-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="84e8a-115">Aby formularz był widoczny dla modelu COM, należy dodać <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutów do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="84e8a-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5. <span data-ttu-id="84e8a-116">Implementuje właściwości publiczne lub metody w kodzie aplikacji, która będzie używana w kodzie skryptu.</span><span class="sxs-lookup"><span data-stu-id="84e8a-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="84e8a-117">Na przykład jeśli używasz klasy formularza dla skryptów obiektu, Dodaj następujący kod do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="84e8a-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6. <span data-ttu-id="84e8a-118">Użyj `window.external` obiektu w kodzie skryptu do publicznej właściwości i metody określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="84e8a-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="84e8a-119">Poniższy kod HTML przedstawia sposób wywołania metody wobec obiektu skryptów od kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="84e8a-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="84e8a-120">Skopiuj ten kod do elementu BODY dokumentu HTML, który należy załadować przy użyciu formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="84e8a-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7. <span data-ttu-id="84e8a-121">Implementowanie funkcji w kodzie skryptu, który będzie używany w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="84e8a-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="84e8a-122">Następujący element HTML skrypt zawiera przykład funkcja.</span><span class="sxs-lookup"><span data-stu-id="84e8a-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="84e8a-123">Skopiuj ten kod w element główny dokumentu HTML, który należy załadować przy użyciu formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="84e8a-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8. <span data-ttu-id="84e8a-124">Użyj <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości dostępu do kodu skryptu w kodzie aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="84e8a-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="84e8a-125">Na przykład, Dodaj następujący kod do przycisku <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="84e8a-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="84e8a-126">Po zakończeniu debugowania usługi DHTML ustawić <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> właściwości `true` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlanie komunikatów o błędach dla problemów kodu skryptu.</span><span class="sxs-lookup"><span data-stu-id="84e8a-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="84e8a-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="84e8a-127">Example</span></span>  
 <span data-ttu-id="84e8a-128">Poniższy przykład kompletny kod zapewnia aplikacji demonstracyjnych, która umożliwia zrozumienie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="84e8a-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="84e8a-129">Kod HTML jest ładowany do <xref:System.Windows.Forms.WebBrowser> kontrolować za pośrednictwem <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości zamiast ładowana z pliku HTML.</span><span class="sxs-lookup"><span data-stu-id="84e8a-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84e8a-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="84e8a-130">Compiling the Code</span></span>  
 <span data-ttu-id="84e8a-131">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="84e8a-131">This code requires:</span></span>  
  
- <span data-ttu-id="84e8a-132">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="84e8a-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="84e8a-133">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="84e8a-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="84e8a-134">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="84e8a-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e8a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84e8a-135">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="84e8a-136">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="84e8a-136">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
