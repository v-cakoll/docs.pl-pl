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
ms.openlocfilehash: 26cbc995a749c4c129729be700dee588d1033a05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953437"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="3459e-102">Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML a kodem aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="3459e-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>

<span data-ttu-id="3459e-103">Za pomocą <xref:System.Windows.Forms.WebBrowser> kontrolki można dodać istniejący kod aplikacji sieci Web (DHTML) do Windows Forms aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="3459e-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="3459e-104">Jest to przydatne, gdy zainwestowano znaczący czas projektowania podczas tworzenia formantów opartych na języku DHTML i chcesz korzystać z zaawansowanych możliwości interfejsu użytkownika Windows Forms bez konieczności ponownego zapisywania istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="3459e-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>

<span data-ttu-id="3459e-105">Kontrolka umożliwia zaimplementowanie dwukierunkowej komunikacji między kodem aplikacji klienta i kodem skryptowym strony sieci Web <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> za pomocą <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości i. <xref:System.Windows.Forms.WebBrowser></span><span class="sxs-lookup"><span data-stu-id="3459e-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="3459e-106">Ponadto można skonfigurować <xref:System.Windows.Forms.WebBrowser> kontrolkę tak, aby kontrolki sieci Web bezproblemowo mieszają się z innymi kontrolkami w formularzu aplikacji, ukrywając ich implementację DHTML.</span><span class="sxs-lookup"><span data-stu-id="3459e-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="3459e-107">Aby bezproblemowo mieszać kontrolki, sformatuj wyświetlaną stronę tak, aby jej kolor tła i styl wizualny odpowiadały pozostałej części formularza <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>i Użyj <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości, i, aby wyłączyć standardowe funkcje przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="3459e-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="3459e-108">Aby osadzić DHTML w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3459e-108">To embed DHTML in your Windows Forms application</span></span>

1. <span data-ttu-id="3459e-109"><xref:System.Windows.Forms.WebBrowser> Ustaw <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> Właściwośćkontrolki`false` na, aby uniemożliwić kontrolowanie<xref:System.Windows.Forms.WebBrowser> otwierania plików.</span><span class="sxs-lookup"><span data-stu-id="3459e-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. <span data-ttu-id="3459e-110">Ustaw <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> właściwość kontrolki na `false` , aby zapobiec <xref:System.Windows.Forms.WebBrowser> wyświetlaniu menu skrótów przez formant po kliknięciu go prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="3459e-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. <span data-ttu-id="3459e-111">Ustaw <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwość kontrolki na `false` , aby uniemożliwić <xref:System.Windows.Forms.WebBrowser> sterowanie odpowiedzią na skróty klawiaturowe.</span><span class="sxs-lookup"><span data-stu-id="3459e-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. <span data-ttu-id="3459e-112">Ustaw właściwość w Konstruktorze formularza <xref:System.Windows.Forms.Form.Load> lub programie obsługi zdarzeń. <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A></span><span class="sxs-lookup"><span data-stu-id="3459e-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>

     <span data-ttu-id="3459e-113">Poniższy kod używa samej klasy form dla obiektu Scripting.</span><span class="sxs-lookup"><span data-stu-id="3459e-113">The following code uses the form class itself for the scripting object.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3459e-114">Component Object Model (COM) musi być w stanie uzyskać dostęp do obiektu skryptów.</span><span class="sxs-lookup"><span data-stu-id="3459e-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="3459e-115">Aby formularz był widoczny dla modelu COM, Dodaj <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="3459e-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. <span data-ttu-id="3459e-116">Implementowanie publicznych właściwości lub metod w kodzie aplikacji, który będzie używany przez kod skryptu.</span><span class="sxs-lookup"><span data-stu-id="3459e-116">Implement public properties or methods in your application code that your script code will use.</span></span>

     <span data-ttu-id="3459e-117">Na przykład, jeśli używasz klasy form dla obiektu Scripting, Dodaj następujący kod do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="3459e-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. <span data-ttu-id="3459e-118">`window.external` Użyj obiektu w kodzie skryptów, aby uzyskać dostęp do publicznych właściwości i metod określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3459e-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>

     <span data-ttu-id="3459e-119">Poniższy kod HTML demonstruje sposób wywołania metody dla obiektu skryptu z kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="3459e-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="3459e-120">Skopiuj ten kod do elementu body dokumentu HTML, który jest ładowany przy użyciu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody kontrolki lub przypisanej do <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3459e-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. <span data-ttu-id="3459e-121">Zaimplementuj funkcje w kodzie skryptu, który będzie używany przez kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3459e-121">Implement functions in your script code that your application code will use.</span></span>

     <span data-ttu-id="3459e-122">Poniższy element skryptu HTML zawiera przykład funkcji.</span><span class="sxs-lookup"><span data-stu-id="3459e-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="3459e-123">Skopiuj ten kod do elementu nagłówkowego dokumentu HTML, który jest ładowany przy użyciu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody kontrolki lub przypisanej do <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3459e-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. <span data-ttu-id="3459e-124"><xref:System.Windows.Forms.WebBrowser.Document%2A> Użyj właściwości, aby uzyskać dostęp do kodu skryptu z kodu aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="3459e-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>

     <span data-ttu-id="3459e-125">Na przykład Dodaj następujący kod do programu obsługi zdarzeń przycisku <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="3459e-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. <span data-ttu-id="3459e-126">Po zakończeniu debugowania kodu DHTML Ustaw <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> właściwość kontrolki na `true` , aby zapobiec <xref:System.Windows.Forms.WebBrowser> wyświetlaniu przez formant komunikatów o błędach w przypadku problemów z kodem skryptu.</span><span class="sxs-lookup"><span data-stu-id="3459e-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a><span data-ttu-id="3459e-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="3459e-127">Example</span></span>

<span data-ttu-id="3459e-128">Poniższy pełny kod zawiera przykładową aplikację, której można użyć do zrozumienia tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3459e-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="3459e-129">Kod HTML jest ładowany do <xref:System.Windows.Forms.WebBrowser> kontrolki <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> za pośrednictwem właściwości zamiast ładowania z oddzielnego pliku HTML.</span><span class="sxs-lookup"><span data-stu-id="3459e-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="3459e-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3459e-130">Compiling the Code</span></span>

<span data-ttu-id="3459e-131">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="3459e-131">This code requires:</span></span>

- <span data-ttu-id="3459e-132">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="3459e-132">References to the System and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="3459e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3459e-133">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3459e-134">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3459e-134">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
