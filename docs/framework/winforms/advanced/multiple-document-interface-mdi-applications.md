---
title: "Aplikacje interfejsu wielu dokumentów (MDI)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74735afcb1d6be319ad5d497615a3b725a4d5574
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplikacje interfejsu wielu dokumentów (MDI)
Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, każdy dokument wyświetlany w osobnym oknie. MDI — aplikacje często mają elementu menu okna zawierającego podmenu do przełączania między systemem windows lub dokumenty.  
  
> [!NOTE]
>  Istnieją pewne różnice zachowanie między formularze MDI i interfejsu pojedynczego dokumentu (SDI) systemu windows w formularzach systemu Windows. `Opacity` Właściwość nie ma wpływu na wyglądu formularzy podrzędnych MDI. Ponadto <xref:System.Windows.Forms.Form.CenterToParent%2A> — metoda nie ma wpływu na zachowanie formularzy podrzędnych MDI.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.  
  
 [Instrukcje: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 Zawiera wskazówki dotyczące tworzenia co najmniej jednego systemu windows, które działają w ramach formularza nadrzędnego MDI.  
  
 [Instrukcje: określanie elementu podrzędnego MDI Active](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 Zawiera wskazówki dotyczące weryfikacji okno podrzędne, które ma fokus (i wysyłanie zawartości do Schowka).  
  
 [Instrukcje: wysyłanie danych do Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 Zawiera wskazówki dotyczące informacji do okna aktywny transport.  
  
 [Instrukcje: aranżowanie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 Zapewnia instrukcje dla kafelków, kaskadowych lub rozmieszczanie okien podrzędnych MDI aplikacji.
