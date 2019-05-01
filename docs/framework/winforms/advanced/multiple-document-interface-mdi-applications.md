---
title: Aplikacje interfejsu wielu dokumentów (MDI)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952051"
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplikacje interfejsu wielu dokumentów (MDI)
Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wiele dokumentów w tym samym czasie za pomocą każdy dokument wyświetlany w osobnym oknie. Aplikacje MDI często mają element menu Okno oraz podmenu do przełączania się między systemem windows lub dokumenty.  
  
> [!NOTE]
>  Istnieją pewne różnice zachowanie między formularze MDI i interfejsu pojedynczego dokumentu (SDI) systemu windows w formularzach Windows Forms. `Opacity` Właściwość nie ma wpływu na wygląd formularzy podrzędnych MDI. Ponadto <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nie ma wpływu na zachowanie formularzy podrzędnych MDI.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)  
 Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.  
  
 [Instrukcje: Tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)  
 Zawiera wskazówki dotyczące tworzenia co najmniej systemu windows, które działają w ramach formularza nadrzędnego MDI.  
  
 [Instrukcje: Określanie elementu podrzędnego Active MDI](how-to-determine-the-active-mdi-child.md)  
 Zawiera wskazówki dotyczące weryfikacji okna podrzędnego, który ma fokus (i wysyła jego zawartość do Schowka).  
  
 [Instrukcje: Wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)  
 Zawiera wskazówki dotyczące transportowania informacji do okna podrzędnego active.  
  
 [Instrukcje: Aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)  
 Zawiera wskazówki dla fragmentacji, kaskadowych lub rozmieszczanie okien podrzędnych MDI aplikacji.
