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
ms.openlocfilehash: 8767ef0fb484d43ffad4888affebb9d6bb74cc3a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384643"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="6476e-102">Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="6476e-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="6476e-103">Zarządzany HTML Document Object Model (DOM) zawiera klasę o nazwie <xref:System.Windows.Forms.HtmlElement> który udostępnia właściwości, metody i zdarzenia, mających wspólne wszystkich elementów HTML.</span><span class="sxs-lookup"><span data-stu-id="6476e-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="6476e-104">Czasami jednak konieczne będzie dostęp do elementów członkowskich, które zarządzanego interfejsu bezpośrednio nie ujawnia.</span><span class="sxs-lookup"><span data-stu-id="6476e-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="6476e-105">W tym temacie analizuje dwa sposoby uzyskania dostępu do nieujawnionych elementów, w tym [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] i funkcje VBScript, zdefiniowane wewnątrz strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6476e-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="6476e-106">Uzyskiwanie dostępu do nieujawnionych elementów w modelu za pośrednictwem interfejsów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="6476e-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="6476e-107"><xref:System.Windows.Forms.HtmlDocument> i <xref:System.Windows.Forms.HtmlElement> zapewnia cztery metody, które umożliwiają dostęp do nieujawnionych elementów w modelu.</span><span class="sxs-lookup"><span data-stu-id="6476e-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="6476e-108">W poniższej tabeli przedstawiono typy i odpowiadającej im metody.</span><span class="sxs-lookup"><span data-stu-id="6476e-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="6476e-109">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="6476e-109">Member Type</span></span>|<span data-ttu-id="6476e-110">Metody</span><span class="sxs-lookup"><span data-stu-id="6476e-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6476e-111">Właściwości (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="6476e-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="6476e-112">Metody</span><span class="sxs-lookup"><span data-stu-id="6476e-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="6476e-113">Zdarzenia (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="6476e-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="6476e-114">Zdarzenia (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="6476e-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="6476e-115">Zdarzenia (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="6476e-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="6476e-116">Korzystając z tych metod, zakłada się, że masz element poprawnego typu bazowego.</span><span class="sxs-lookup"><span data-stu-id="6476e-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="6476e-117">Załóżmy, że chcesz posłuchać `Submit` zdarzenia `FORM` elementu HTML strony, dzięki czemu możesz wykonać niektóre wstępne przetwarzanie na `FORM`firmy wartości, zanim użytkownik przesyła je do serwera.</span><span class="sxs-lookup"><span data-stu-id="6476e-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="6476e-118">Najlepiej, jeśli masz kontrolę nad HTML, zdefiniujesz `FORM` mieć unikatową `ID` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6476e-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
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
  
 <span data-ttu-id="6476e-119">Po załadowaniu tej strony do <xref:System.Windows.Forms.WebBrowser> kontrolki, można użyć <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metodę, która pobierze `FORM` w czasie wykonywania za pomocą `form1` jako argument.</span><span class="sxs-lookup"><span data-stu-id="6476e-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="6476e-120">Uzyskiwanie dostępu do niezarządzanych interfejsów</span><span class="sxs-lookup"><span data-stu-id="6476e-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="6476e-121">Po niezarządzane interfejsy Component Object Model (COM) udostępniane przez każdej klasy modelu DOM, dostęp do nieujawnionych elementów zarządzany HTML DOM.</span><span class="sxs-lookup"><span data-stu-id="6476e-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="6476e-122">Jest to zalecane, jeśli konieczne będzie wprowadzenie kilku wywołaniami nieujawnionych elementów lub jeśli nieujawnionych elementów zwrócić inne interfejsy niezarządzane nie zostały opakowane przez zarządzany HTML DOM</span><span class="sxs-lookup"><span data-stu-id="6476e-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="6476e-123">W poniższej tabeli przedstawiono wszystkie niezarządzane interfejsy, które są udostępniane za pośrednictwem zarządzanej HTML DOM.</span><span class="sxs-lookup"><span data-stu-id="6476e-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="6476e-124">Kliknij pozycję w każdym odnośniku objaśnienia dotyczące jego użycia, a przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="6476e-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="6476e-125">Typ</span><span class="sxs-lookup"><span data-stu-id="6476e-125">Type</span></span>|<span data-ttu-id="6476e-126">Niezarządzany interfejs</span><span class="sxs-lookup"><span data-stu-id="6476e-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="6476e-127">Najprostszym sposobem korzystania z interfejsów COM jest dodać odwołanie do biblioteki niezarządzanej HTML DOM (MSHTML.dll) z aplikacji, chociaż jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6476e-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="6476e-128">Aby uzyskać więcej informacji, zobacz [934368 artykuł bazy wiedzy Knowledge Base](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="6476e-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="6476e-129">Uzyskiwanie dostępu do funkcji skryptu</span><span class="sxs-lookup"><span data-stu-id="6476e-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="6476e-130">Na stronie HTML można zdefiniować jedną lub więcej funkcji za pomocą języka skryptów, takich jak [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] lub VBScript.</span><span class="sxs-lookup"><span data-stu-id="6476e-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="6476e-131">Te funkcje są umieszczone wewnątrz `SCRIPT` strony na stronie, a może działać na żądanie lub w odpowiedzi na zdarzenie w DOM.</span><span class="sxs-lookup"><span data-stu-id="6476e-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="6476e-132">Możesz wywołać wszystkie funkcje skrypt, należy zdefiniować strony HTML przy użyciu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6476e-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="6476e-133">Jeśli metoda skrypt zwraca HTML element, można użyć rzutowania, można przekonwertować ten wynik zwracany <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="6476e-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="6476e-134">Aby uzyskać szczegółowe informacje i przykładowy kod, zobacz <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="6476e-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6476e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6476e-135">See Also</span></span>  
 [<span data-ttu-id="6476e-136">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="6476e-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
