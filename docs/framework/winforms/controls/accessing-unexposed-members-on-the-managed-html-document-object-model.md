---
title: Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988399"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="6b85a-102">Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="6b85a-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="6b85a-103">Zarządzany Document Object Model HTML (dom) zawiera klasę o nazwie <xref:System.Windows.Forms.HtmlElement> , która uwidacznia właściwości, metody i zdarzenia, które są wspólne dla wszystkich elementów HTML.</span><span class="sxs-lookup"><span data-stu-id="6b85a-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="6b85a-104">Czasami jednak konieczne będzie uzyskanie dostępu do elementów członkowskich, które nie ujawniają bezpośrednio w interfejsie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6b85a-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="6b85a-105">W tym temacie przedstawiono dwa sposoby uzyskiwania dostępu do nieujawnionych członków, w tym funkcji JScript i VBScript zdefiniowanych wewnątrz strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6b85a-105">This topic examines two ways for accessing unexposed members, including JScript and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="6b85a-106">Uzyskiwanie dostępu do nieujawnionych członków za poorednictwem interfejsów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="6b85a-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="6b85a-107"><xref:System.Windows.Forms.HtmlDocument>i <xref:System.Windows.Forms.HtmlElement> zapewniają cztery metody umożliwiające dostęp do nieujawnionych członków.</span><span class="sxs-lookup"><span data-stu-id="6b85a-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="6b85a-108">W poniższej tabeli przedstawiono typy i odpowiadające im metody.</span><span class="sxs-lookup"><span data-stu-id="6b85a-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="6b85a-109">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="6b85a-109">Member Type</span></span>|<span data-ttu-id="6b85a-110">Metody (s)</span><span class="sxs-lookup"><span data-stu-id="6b85a-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6b85a-111">Właściwości (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="6b85a-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="6b85a-112">Metody</span><span class="sxs-lookup"><span data-stu-id="6b85a-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="6b85a-113">Zdarzenia (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="6b85a-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="6b85a-114">Zdarzenia (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="6b85a-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="6b85a-115">Zdarzenia (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="6b85a-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="6b85a-116">Korzystając z tych metod, zakłada się, że masz element poprawnego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="6b85a-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="6b85a-117">Załóżmy, że chcesz nasłuchiwać `Submit` zdarzenia `FORM` elementu na stronie HTML, dzięki czemu można wykonać `FORM`wstępne przetwarzanie na wartościach, zanim użytkownik prześle je do serwera.</span><span class="sxs-lookup"><span data-stu-id="6b85a-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="6b85a-118">Najlepiej, jeśli masz kontrolę nad kodem HTML, zdefiniujesz `FORM` , aby mieć unikatowy `ID` atrybut.</span><span class="sxs-lookup"><span data-stu-id="6b85a-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```html  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 <span data-ttu-id="6b85a-119">Po <xref:System.Windows.Forms.WebBrowser> załadowaniu tej strony do formantu można <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> użyć metody, aby pobrać `FORM` w czasie wykonywania za pomocą `form1` jako argument.</span><span class="sxs-lookup"><span data-stu-id="6b85a-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="6b85a-120">Uzyskiwanie dostępu do interfejsów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="6b85a-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="6b85a-121">Możesz również uzyskać dostęp do nieujawnionych członków w zarządzanym modelu HTML DOM przy użyciu niezarządzanych interfejsów Component Object Model (COM) uwidocznionych przez poszczególne klasy DOM.</span><span class="sxs-lookup"><span data-stu-id="6b85a-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="6b85a-122">Jest to zalecane, jeśli trzeba wykonać kilka wywołań dla niewidocznych elementów członkowskich lub jeśli nieujawnione elementy członkowskie zwracają inne niezarządzane interfejsy, które nie są opakowane przez zarządzany DOM HTML.</span><span class="sxs-lookup"><span data-stu-id="6b85a-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="6b85a-123">W poniższej tabeli przedstawiono wszystkie niezarządzane interfejsy uwidocznione za pomocą zarządzanego modelu DOM języka HTML.</span><span class="sxs-lookup"><span data-stu-id="6b85a-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="6b85a-124">Kliknij każdy link, aby uzyskać wyjaśnienie jego użycia i przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="6b85a-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="6b85a-125">Typ</span><span class="sxs-lookup"><span data-stu-id="6b85a-125">Type</span></span>|<span data-ttu-id="6b85a-126">Niezarządzany interfejs</span><span class="sxs-lookup"><span data-stu-id="6b85a-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="6b85a-127">Najprostszym sposobem korzystania z interfejsów COM jest dodanie odwołania do niezarządzanej biblioteki DOM HTML (MSHTML. dll) z aplikacji, chociaż nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6b85a-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="6b85a-128">Aby uzyskać więcej informacji, zobacz [artykuł w bazie wiedzy 934368](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="6b85a-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="6b85a-129">Uzyskiwanie dostępu do funkcji skryptu</span><span class="sxs-lookup"><span data-stu-id="6b85a-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="6b85a-130">Strona HTML może zdefiniować co najmniej jedną funkcję przy użyciu języka skryptowego, takiego jak JScript lub VBScript.</span><span class="sxs-lookup"><span data-stu-id="6b85a-130">An HTML page can define one or more functions by using a scripting language such as JScript or VBScript.</span></span> <span data-ttu-id="6b85a-131">Te funkcje są umieszczane wewnątrz `SCRIPT` strony na stronie i mogą być uruchamiane na żądanie lub w odpowiedzi na zdarzenie w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="6b85a-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="6b85a-132">Można wywołać wszystkie funkcje skryptów zdefiniowane na stronie HTML przy użyciu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6b85a-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="6b85a-133">Jeśli metoda skryptu zwraca element HTML, można użyć rzutowania, aby przekonwertować ten wynik zwracany do <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="6b85a-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="6b85a-134">Aby uzyskać szczegółowe informacje i przykładowy kod <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="6b85a-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b85a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b85a-135">See also</span></span>

- [<span data-ttu-id="6b85a-136">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="6b85a-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
