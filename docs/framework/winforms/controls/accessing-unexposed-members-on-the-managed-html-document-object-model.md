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
ms.openlocfilehash: 20341a44eb8a43a9d130e0b76d23b513738c6782
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011899"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Zarządzany HTML Document Object Model (DOM) zawiera klasę o nazwie <xref:System.Windows.Forms.HtmlElement> który udostępnia właściwości, metody i zdarzenia, mających wspólne wszystkich elementów HTML. Czasami jednak konieczne będzie dostęp do elementów członkowskich, które zarządzanego interfejsu bezpośrednio nie ujawnia. W tym temacie analizuje dwa sposoby uzyskania dostępu do nieujawnionych elementów, w tym [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] i funkcje VBScript, zdefiniowane wewnątrz strony sieci Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Uzyskiwanie dostępu do nieujawnionych elementów w modelu za pośrednictwem interfejsów zarządzanych  
 <xref:System.Windows.Forms.HtmlDocument> i <xref:System.Windows.Forms.HtmlElement> zapewnia cztery metody, które umożliwiają dostęp do nieujawnionych elementów w modelu. W poniższej tabeli przedstawiono typy i odpowiadającej im metody.  
  
|Typ elementu członkowskiego|Metody|  
|-----------------|-----------------|  
|Właściwości (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Metody|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Zdarzenia (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Korzystając z tych metod, zakłada się, że masz element poprawnego typu bazowego. Załóżmy, że chcesz posłuchać `Submit` zdarzenia `FORM` elementu HTML strony, dzięki czemu możesz wykonać niektóre wstępne przetwarzanie na `FORM`firmy wartości, zanim użytkownik przesyła je do serwera. Najlepiej, jeśli masz kontrolę nad HTML, zdefiniujesz `FORM` mieć unikatową `ID` atrybutu.  
  
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
  
 Po załadowaniu tej strony do <xref:System.Windows.Forms.WebBrowser> kontrolki, można użyć <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metodę, która pobierze `FORM` w czasie wykonywania za pomocą `form1` jako argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Uzyskiwanie dostępu do niezarządzanych interfejsów  
 Po niezarządzane interfejsy Component Object Model (COM) udostępniane przez każdej klasy modelu DOM, dostęp do nieujawnionych elementów zarządzany HTML DOM. Jest to zalecane, jeśli konieczne będzie wprowadzenie kilku wywołaniami nieujawnionych elementów lub jeśli nieujawnionych elementów zwrócić inne interfejsy niezarządzane nie zostały opakowane przez zarządzany HTML DOM  
  
 W poniższej tabeli przedstawiono wszystkie niezarządzane interfejsy, które są udostępniane za pośrednictwem zarządzanej HTML DOM. Kliknij pozycję w każdym odnośniku objaśnienia dotyczące jego użycia, a przykład kodu.  
  
|Typ|Niezarządzany interfejs|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Najprostszym sposobem korzystania z interfejsów COM jest dodać odwołanie do biblioteki niezarządzanej HTML DOM (MSHTML.dll) z aplikacji, chociaż jest to obsługiwane. Aby uzyskać więcej informacji, zobacz [934368 artykuł bazy wiedzy Knowledge Base](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Uzyskiwanie dostępu do funkcji skryptu  
 Na stronie HTML można zdefiniować jedną lub więcej funkcji za pomocą języka skryptów, takich jak [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] lub VBScript. Te funkcje są umieszczone wewnątrz `SCRIPT` strony na stronie, a może działać na żądanie lub w odpowiedzi na zdarzenie w DOM.  
  
 Możesz wywołać wszystkie funkcje skrypt, należy zdefiniować strony HTML przy użyciu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody. Jeśli metoda skrypt zwraca HTML element, można użyć rzutowania, można przekonwertować ten wynik zwracany <xref:System.Windows.Forms.HtmlElement>. Aby uzyskać szczegółowe informacje i przykładowy kod, zobacz <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML](using-the-managed-html-document-object-model.md)
