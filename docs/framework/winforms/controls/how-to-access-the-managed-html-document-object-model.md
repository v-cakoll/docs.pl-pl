---
title: 'Instrukcje: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 04d5f9e6f128d9b4ed3f07a5faebe06ae4ffdebf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315195"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Instrukcje: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Dostęp z zarządzanego HTML Document Object Model (DOM), spośród dwóch rodzajów aplikacji:  
  
-   Aplikacji Windows Forms (.exe), która obsługiwana zarządzanej <xref:System.Windows.Forms.WebBrowser> kontroli. Te dwie technologie wzajemnie się uzupełniają, za pomocą <xref:System.Windows.Forms.WebBrowser> kontroli stroną dla użytkownika i HTML DOM reprezentującej strukturę logiczną dokumentu.  
  
-   Formularze Windows <xref:System.Windows.Forms.UserControl> hostowany w programie Internet Explorer. Możesz uzyskać dostęp DOM HTML reprezentujący stronę, na którym Twojej <xref:System.Windows.Forms.UserControl> znajduje się w celu zmiany struktury dokumentu lub Otwórz modalnych okien dialogowych, wśród wielu innych możliwości.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Aby uzyskać dostęp do modelu DOM z aplikacji Windows Forms  
  
1. Host <xref:System.Windows.Forms.WebBrowser> kontrolki w aplikacji Windows Forms i Monitoruj <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń. Szczegółowe informacje na temat kontrolki hostingu i monitorowania zdarzeń, [zdarzenia](../../../standard/events/index.md).  
  
2. Pobieranie <xref:System.Windows.Forms.HtmlDocument> dla bieżącej strony, uzyskując dostęp do <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> kontroli.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Dostęp do modelu DOM z elementu UserControl hostowanych w programie Internet Explorer  
  
1. Utwórz własne niestandardowe klasy pochodnej <xref:System.Windows.Forms.UserControl> klasy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie kontrolek złożonych](how-to-author-composite-controls.md).  
  
2. Umieść następujący kod wewnątrz procedury obsługi zdarzenia obciążenia dla swojej <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
1. Podczas korzystania z modelu DOM przy użyciu <xref:System.Windows.Forms.WebBrowser> kontrolki, należy zawsze poczekać aż <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> wystąpi zdarzenie przed podjęciem próby uzyskania dostępu <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> kontroli. <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Zdarzenie jest wywoływane po załadowaniu całego dokumentu; Jeśli używasz modelu DOM przed tym dniem, istnieje ryzyko powoduje wyjątek czasu wykonywania w aplikacji.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
  
1. Aplikacja lub <xref:System.Windows.Forms.UserControl> będzie wymagać pełnego zaufania w celu uzyskania dostępu do zarządzanego kodu HTML DOM. Jeżeli wdrażasz aplikacji Windows Forms przy użyciu [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], możesz poprosić o pełnym zaufaniu przy użyciu zaufanego wdrożenia aplikacji lub podnoszenia poziomu uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications) Aby uzyskać szczegółowe informacje.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML](using-the-managed-html-document-object-model.md)
