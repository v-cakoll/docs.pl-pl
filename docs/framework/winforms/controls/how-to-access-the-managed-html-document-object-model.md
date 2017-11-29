---
title: "Porady: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML"
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
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 284bd30a0a42f245c6b75d916853b264c7f72e6a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Porady: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Zarządzany HTML modelu DOM (Document Object) mogą korzystać z dwóch typów aplikacji:  
  
-   Aplikacji formularzy systemu Windows (.exe), który hostował zarządzanej <xref:System.Windows.Forms.WebBrowser> formantu. Te dwie technologie uzupełnić, <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlania strony do modelu DOM kodu HTML reprezentujący struktury logicznej dokumentu i użytkownika.  
  
-   Formularze systemu Windows <xref:System.Windows.Forms.UserControl> hostowanej w programie Internet Explorer. Można uzyskać dostępu do modelu DOM kodu HTML reprezentujący strony, na której Twojej <xref:System.Windows.Forms.UserControl> znajduje się w celu zmiany struktury dokumentu lub Otwórz modalnych okien dialogowych, wśród innych możliwości.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Dostępu do modelu DOM w aplikacji formularzy systemu Windows  
  
1.  Host <xref:System.Windows.Forms.WebBrowser> kontroli w aplikacji formularzy systemu Windows oraz monitorować <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń. Szczegółowe informacje o kontrole hostingu i monitorowanie zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).  
  
2.  Pobrać <xref:System.Windows.Forms.HtmlDocument> dla bieżącej strony, uzyskując dostęp do <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> formantu.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Dostęp do modelu DOM z elementu UserControl hostowanej w programie Internet Explorer  
  
1.  Tworzenie własnych niestandardowych klasy pochodnej <xref:System.Windows.Forms.UserControl> klasy. Aby uzyskać więcej informacji, zobacz [porady: formanty złożone autora](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).  
  
2.  Umieść następujący kod wewnątrz obsługi zdarzenia obciążenia dla Twojego <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
1.  Korzystając z modelu DOM za pośrednictwem <xref:System.Windows.Forms.WebBrowser> kontroli, użytkownik powinien zawsze czekać <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzenie przed podjęciem próby uzyskania dostępu <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> formantu. <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Zdarzenie jest wywoływane po załadowaniu całego dokumentu; Jeśli używasz modelu DOM przed upływem, istnieje ryzyko spowodować wyjątek czasu wykonywania w aplikacji.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
  
1.  Aplikacja lub <xref:System.Windows.Forms.UserControl> będzie wymagają pełnego zaufania, aby uzyskać dostęp do zarządzany HTML DOM Jeśli wdrażasz aplikacji formularzy systemu Windows przy użyciu [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], możesz poprosić o pełnego zaufania przy użyciu podniesienia uprawnień lub zaufanych wdrożenia aplikacji, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications) szczegółowe informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą modelu obiektów zarządzanych dokumentów HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
