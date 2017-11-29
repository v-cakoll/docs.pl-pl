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
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Zarządzany HTML modelu DOM (Document Object) zawiera klasy o nazwie <xref:System.Windows.Forms.HtmlElement> która udostępnia właściwości, metod i zdarzeń, mających wspólne wszystkich elementów HTML. Czasami jednak konieczne będzie dostęp do elementów członkowskich, które zarządzanego interfejsu bezpośrednio nie ujawnia. W tym temacie sprawdza, czy dwa sposoby do uzyskiwania dostępu do nieujawnionych elementów członkowskich, w tym [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] i funkcji VBScript, zdefiniowane wewnątrz strony sieci Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Uzyskiwanie dostępu do nieujawnionych elementów członkowskich za pomocą zarządzanych interfejsów  
 <xref:System.Windows.Forms.HtmlDocument>i <xref:System.Windows.Forms.HtmlElement> podać cztery metody, które umożliwiają dostęp do nieujawnionych elementów członkowskich. W poniższej tabeli przedstawiono typy oraz ich odpowiednich metod.  
  
|Typ elementu członkowskiego|Metody|  
|-----------------|-----------------|  
|Właściwości (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Metody|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Korzystając z tych metod, zakłada się, że element poprawnego typu podstawowego. Załóżmy, że chcesz posłuchać `Submit` zdarzenie `FORM` elementu HTML strony tak, aby można było wykonać niektóre przetwarzanie wstępne na `FORM`na wartości, zanim użytkownik przesyła je do serwera. Najlepiej, jeśli masz kontrolę nad HTML, należy zdefiniować `FORM` mieć unikatową `ID` atrybutu.  
  
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
  
 Po załadowaniu tej strony do <xref:System.Windows.Forms.WebBrowser> sterowania, można użyć <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metoda pobierania `FORM` w czasie wykonywania za pomocą `form1` jako argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Uzyskiwanie dostępu do interfejsów niezarządzane  
 Można także przejść nieujawnionych elementów w zarządzany HTML DOM przy użyciu niezarządzane interfejsy modelu COM (Component Object) udostępniane przez każdej klasy modelu DOM. Jest to zalecane, jeśli masz wiele wywołań przed nieujawnionych elementów członkowskich lub gdy nieujawnione elementy Członkowskie zwracają inne interfejsy niezarządzane nie zostały opakowane przez zarządzany HTML DOM  
  
 W poniższej tabeli przedstawiono wszystkie interfejsy niezarządzane, za pośrednictwem zarządzany HTML DOM Kliknij każde łącze, aby uzyskać informacje o jego użycia i na przykład kodu.  
  
|Typ|Niezarządzane — interfejs|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Najprostszym sposobem korzystania z interfejsów COM jest dodanie odwołania do niezarządzanego biblioteki HTML DOM (MSHTML.dll) z aplikacji, chociaż jest to obsługiwane. Aby uzyskać więcej informacji, zobacz [934368 artykułu bazy wiedzy Knowledge Base](http://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Uzyskiwanie dostępu do funkcji skryptu  
 Strona HTML można określić jedną lub więcej funkcji przy użyciu języka skryptów, takich jak [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] lub VBScript. Te funkcje są umieszczone wewnątrz `SCRIPT` strony na stronie i mogą być uruchamiane na żądanie lub w odpowiedzi na zdarzenia w modelu DOM.  
  
 Możesz wywołać wszystkie funkcje skryptu można zdefiniować na stronie HTML za pomocą <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody. Jeśli skrypt zwraca HTML element, umożliwia rzutowanie Konwertuj ten wynik zwracany <xref:System.Windows.Forms.HtmlElement>. Aby uzyskać szczegółowe informacje i przykładowy kod, zobacz <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą modelu obiektów zarządzanych dokumentów HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
