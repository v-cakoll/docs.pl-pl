---
title: "Porady: implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta"
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ad99683f0e41e64a42032a9d64e589723fa8ed4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="3486c-102">Porady: implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="3486c-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="3486c-103">Można użyć <xref:System.Windows.Forms.WebBrowser> formantu, aby dodać istniejące dynamiczny kod aplikacji sieci Web HTML (DHTML) aplikacjom klienckim formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3486c-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="3486c-104">Jest to przydatne, gdy zainwestowały czasu znaczących programowania do tworzenia opartych na DHTML — formanty i chcesz korzystać z funkcji interfejsu użytkownika sformatowanego formularzy systemu Windows bez konieczności ponownego zapisania istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="3486c-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="3486c-105"><xref:System.Windows.Forms.WebBrowser> Kontrola umożliwia Implementowanie dwukierunkowej komunikacji między kod klienta aplikacji i skryptów kodu strony sieci Web za pomocą <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> i <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3486c-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="3486c-106">Ponadto można skonfigurować <xref:System.Windows.Forms.WebBrowser> , aby formantów sieci Web programu blend bezproblemowo z innych kontrolek w formularzu aplikacji, ukrywanie ich realizacji DHTML.</span><span class="sxs-lookup"><span data-stu-id="3486c-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="3486c-107">Na bezproblemowo blend formantów, formatu strony wyświetlany tak, aby jego kolor tła i styl wizualny zgodne pozostałej części formularza i użyj <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, i <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości, aby wyłączyć funkcje standardowej przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="3486c-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="3486c-108">Aby osadzić w aplikacji Windows Forms DHTML</span><span class="sxs-lookup"><span data-stu-id="3486c-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="3486c-109">Ustaw <xref:System.Windows.Forms.WebBrowser> formantu <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików na go.</span><span class="sxs-lookup"><span data-stu-id="3486c-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="3486c-110">Ustawianie formantu <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlanie menu skrótów po kliknięciu go.</span><span class="sxs-lookup"><span data-stu-id="3486c-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="3486c-111">Ustawianie formantu <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> formantu z odpowiada klawiszy skrótu.</span><span class="sxs-lookup"><span data-stu-id="3486c-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="3486c-112">Ustaw <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> właściwości w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3486c-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="3486c-113">W poniższym kodzie użyto samej klasy formularza dla obiekt skryptów.</span><span class="sxs-lookup"><span data-stu-id="3486c-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3486c-114">Składnik modelu COM (Object) musi mieć możliwość dostępu do obiektu skryptów.</span><span class="sxs-lookup"><span data-stu-id="3486c-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="3486c-115">Aby formularz był widoczny dla modelu COM, należy dodać <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu do własnej klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="3486c-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="3486c-116">Implementuje publicznej właściwości i metody w kodzie aplikacji, który będzie używany przez kod skryptu.</span><span class="sxs-lookup"><span data-stu-id="3486c-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="3486c-117">Na przykład jeśli używasz klasy formularza dla obiekt skryptów, Dodaj następujący kod do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="3486c-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="3486c-118">Użyj `window.external` obiektu w kodzie skryptu dostęp do publicznej właściwości i metod określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3486c-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="3486c-119">Poniższy kod HTML pokazano, jak wywołać metody dla obiekt skryptów w kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="3486c-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="3486c-120">Skopiuj ten kod do elementu BODY dokumentu HTML, które zostały załadowane, za pomocą formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3486c-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="3486c-121">Implementowanie funkcji w kodzie skryptu, który będzie używany przez kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3486c-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="3486c-122">Następujący element HTML skryptu zawiera funkcję przykład.</span><span class="sxs-lookup"><span data-stu-id="3486c-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="3486c-123">Skopiuj ten kod do elementu HEAD dokumentu HTML, które zostały załadowane, za pomocą formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3486c-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="3486c-124">Użyj <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości dostępu do kodu skryptu w kodzie aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="3486c-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="3486c-125">Na przykład, Dodaj następujący kod do przycisku <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3486c-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="3486c-126">Po zakończeniu debugowania programu DHTML Ustawianie formantu <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> właściwości `true` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli przy wyświetlaniu komunikatów o błędach dla problemów kodu skryptu.</span><span class="sxs-lookup"><span data-stu-id="3486c-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="3486c-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="3486c-127">Example</span></span>  
 <span data-ttu-id="3486c-128">W poniższym przykładzie kompletny kod zawiera aplikacji demonstracyjnej, która służy do zrozumienia tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3486c-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="3486c-129">Kod HTML jest ładowany do <xref:System.Windows.Forms.WebBrowser> kontrolować za pośrednictwem <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości zamiast ładowana z pliku HTML.</span><span class="sxs-lookup"><span data-stu-id="3486c-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3486c-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3486c-130">Compiling the Code</span></span>  
 <span data-ttu-id="3486c-131">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="3486c-131">This code requires:</span></span>  
  
-   <span data-ttu-id="3486c-132">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3486c-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3486c-133">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3486c-133">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3486c-134">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="3486c-134">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="3486c-135">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3486c-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3486c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3486c-136">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3486c-137">WebBrowser — formant</span><span class="sxs-lookup"><span data-stu-id="3486c-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
