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
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Zarządzany Document Object Model HTML (dom) zawiera klasę o nazwie <xref:System.Windows.Forms.HtmlElement> , która uwidacznia właściwości, metody i zdarzenia, które są wspólne dla wszystkich elementów HTML. Czasami jednak konieczne będzie uzyskanie dostępu do elementów członkowskich, które nie ujawniają bezpośrednio w interfejsie zarządzanym. W tym temacie przedstawiono dwa sposoby uzyskiwania dostępu do nieujawnionych członków, w tym funkcji JScript i VBScript zdefiniowanych wewnątrz strony sieci Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Uzyskiwanie dostępu do nieujawnionych członków za poorednictwem interfejsów zarządzanych  
 <xref:System.Windows.Forms.HtmlDocument>i <xref:System.Windows.Forms.HtmlElement> zapewniają cztery metody umożliwiające dostęp do nieujawnionych członków. W poniższej tabeli przedstawiono typy i odpowiadające im metody.  
  
|Typ elementu członkowskiego|Metody (s)|  
|-----------------|-----------------|  
|Właściwości (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Metody|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Korzystając z tych metod, zakłada się, że masz element poprawnego typu podstawowego. Załóżmy, że chcesz nasłuchiwać `Submit` zdarzenia `FORM` elementu na stronie HTML, dzięki czemu można wykonać `FORM`wstępne przetwarzanie na wartościach, zanim użytkownik prześle je do serwera. Najlepiej, jeśli masz kontrolę nad kodem HTML, zdefiniujesz `FORM` , aby mieć unikatowy `ID` atrybut.  
  
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
  
 Po <xref:System.Windows.Forms.WebBrowser> załadowaniu tej strony do formantu można <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> użyć metody, aby pobrać `FORM` w czasie wykonywania za pomocą `form1` jako argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Uzyskiwanie dostępu do interfejsów niezarządzanych  
 Możesz również uzyskać dostęp do nieujawnionych członków w zarządzanym modelu HTML DOM przy użyciu niezarządzanych interfejsów Component Object Model (COM) uwidocznionych przez poszczególne klasy DOM. Jest to zalecane, jeśli trzeba wykonać kilka wywołań dla niewidocznych elementów członkowskich lub jeśli nieujawnione elementy członkowskie zwracają inne niezarządzane interfejsy, które nie są opakowane przez zarządzany DOM HTML.  
  
 W poniższej tabeli przedstawiono wszystkie niezarządzane interfejsy uwidocznione za pomocą zarządzanego modelu DOM języka HTML. Kliknij każdy link, aby uzyskać wyjaśnienie jego użycia i przykładowego kodu.  
  
|Typ|Niezarządzany interfejs|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Najprostszym sposobem korzystania z interfejsów COM jest dodanie odwołania do niezarządzanej biblioteki DOM HTML (MSHTML. dll) z aplikacji, chociaż nie jest to obsługiwane. Aby uzyskać więcej informacji, zobacz [artykuł w bazie wiedzy 934368](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Uzyskiwanie dostępu do funkcji skryptu  
 Strona HTML może zdefiniować co najmniej jedną funkcję przy użyciu języka skryptowego, takiego jak JScript lub VBScript. Te funkcje są umieszczane wewnątrz `SCRIPT` strony na stronie i mogą być uruchamiane na żądanie lub w odpowiedzi na zdarzenie w modelu DOM.  
  
 Można wywołać wszystkie funkcje skryptów zdefiniowane na stronie HTML przy użyciu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody. Jeśli metoda skryptu zwraca element HTML, można użyć rzutowania, aby przekonwertować ten wynik zwracany do <xref:System.Windows.Forms.HtmlElement>. Aby uzyskać szczegółowe informacje i przykładowy kod <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML](using-the-managed-html-document-object-model.md)
