---
title: "Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML"
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
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda2581ceed854fa5121076f0c7b9df414bffe52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="8e127-102">Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="8e127-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="8e127-103">Zarządzany HTML modelu DOM (Document Object) zawiera klasy o nazwie <xref:System.Windows.Forms.HtmlElement> która udostępnia właściwości, metod i zdarzeń, mających wspólne wszystkich elementów HTML.</span><span class="sxs-lookup"><span data-stu-id="8e127-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="8e127-104">Czasami jednak konieczne będzie dostęp do elementów członkowskich, które zarządzanego interfejsu bezpośrednio nie ujawnia.</span><span class="sxs-lookup"><span data-stu-id="8e127-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="8e127-105">W tym temacie sprawdza, czy dwa sposoby do uzyskiwania dostępu do nieujawnionych elementów członkowskich, w tym [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] i funkcji VBScript, zdefiniowane wewnątrz strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8e127-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="8e127-106">Uzyskiwanie dostępu do nieujawnionych elementów członkowskich za pomocą zarządzanych interfejsów</span><span class="sxs-lookup"><span data-stu-id="8e127-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="8e127-107"><xref:System.Windows.Forms.HtmlDocument>i <xref:System.Windows.Forms.HtmlElement> podać cztery metody, które umożliwiają dostęp do nieujawnionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="8e127-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="8e127-108">W poniższej tabeli przedstawiono typy oraz ich odpowiednich metod.</span><span class="sxs-lookup"><span data-stu-id="8e127-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="8e127-109">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8e127-109">Member Type</span></span>|<span data-ttu-id="8e127-110">Metody</span><span class="sxs-lookup"><span data-stu-id="8e127-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8e127-111">Właściwości (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="8e127-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="8e127-112">Metody</span><span class="sxs-lookup"><span data-stu-id="8e127-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="8e127-113">Zdarzenia (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="8e127-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="8e127-114">Zdarzenia (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="8e127-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="8e127-115">Zdarzenia (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="8e127-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="8e127-116">Korzystając z tych metod, zakłada się, że element poprawnego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8e127-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="8e127-117">Załóżmy, że chcesz posłuchać `Submit` zdarzenie `FORM` elementu HTML strony tak, aby można było wykonać niektóre przetwarzanie wstępne na `FORM`na wartości, zanim użytkownik przesyła je do serwera.</span><span class="sxs-lookup"><span data-stu-id="8e127-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="8e127-118">Najlepiej, jeśli masz kontrolę nad HTML, należy zdefiniować `FORM` mieć unikatową `ID` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8e127-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```  
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
  
 <span data-ttu-id="8e127-119">Po załadowaniu tej strony do <xref:System.Windows.Forms.WebBrowser> sterowania, można użyć <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metoda pobierania `FORM` w czasie wykonywania za pomocą `form1` jako argument.</span><span class="sxs-lookup"><span data-stu-id="8e127-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="8e127-120">Uzyskiwanie dostępu do interfejsów niezarządzane</span><span class="sxs-lookup"><span data-stu-id="8e127-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="8e127-121">Można także przejść nieujawnionych elementów w zarządzany HTML DOM przy użyciu niezarządzane interfejsy modelu COM (Component Object) udostępniane przez każdej klasy modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="8e127-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="8e127-122">Jest to zalecane, jeśli masz wiele wywołań przed nieujawnionych elementów członkowskich lub gdy nieujawnione elementy Członkowskie zwracają inne interfejsy niezarządzane nie zostały opakowane przez zarządzany HTML DOM</span><span class="sxs-lookup"><span data-stu-id="8e127-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="8e127-123">W poniższej tabeli przedstawiono wszystkie interfejsy niezarządzane, za pośrednictwem zarządzany HTML DOM</span><span class="sxs-lookup"><span data-stu-id="8e127-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="8e127-124">Kliknij każde łącze, aby uzyskać informacje o jego użycia i na przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="8e127-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="8e127-125">Typ</span><span class="sxs-lookup"><span data-stu-id="8e127-125">Type</span></span>|<span data-ttu-id="8e127-126">Niezarządzane — interfejs</span><span class="sxs-lookup"><span data-stu-id="8e127-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="8e127-127">Najprostszym sposobem korzystania z interfejsów COM jest dodanie odwołania do niezarządzanego biblioteki HTML DOM (MSHTML.dll) z aplikacji, chociaż jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8e127-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="8e127-128">Aby uzyskać więcej informacji, zobacz [934368 artykułu bazy wiedzy Knowledge Base](http://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="8e127-128">For more information, see [Knowledge Base Article 934368](http://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="8e127-129">Uzyskiwanie dostępu do funkcji skryptu</span><span class="sxs-lookup"><span data-stu-id="8e127-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="8e127-130">Strona HTML można określić jedną lub więcej funkcji przy użyciu języka skryptów, takich jak [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] lub VBScript.</span><span class="sxs-lookup"><span data-stu-id="8e127-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="8e127-131">Te funkcje są umieszczone wewnątrz `SCRIPT` strony na stronie i mogą być uruchamiane na żądanie lub w odpowiedzi na zdarzenia w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="8e127-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="8e127-132">Możesz wywołać wszystkie funkcje skryptu można zdefiniować na stronie HTML za pomocą <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8e127-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="8e127-133">Jeśli skrypt zwraca HTML element, umożliwia rzutowanie Konwertuj ten wynik zwracany <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="8e127-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="8e127-134">Aby uzyskać szczegółowe informacje i przykładowy kod, zobacz <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e127-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e127-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e127-135">See Also</span></span>  
 [<span data-ttu-id="8e127-136">Za pomocą modelu obiektów zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="8e127-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
