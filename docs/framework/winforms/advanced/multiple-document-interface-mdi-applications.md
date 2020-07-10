---
title: Aplikacje interfejsu wielu dokumentów (MDI)
description: Dowiedz się, w jaki sposób Windows Forms aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, z każdym dokumentem wyświetlanym w osobnym oknie.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174656"
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplikacje interfejsu wielu dokumentów (MDI)
Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, przy czym każdy dokument jest wyświetlany w osobnym oknie. Aplikacje MDI często mają element menu okna z podmenumi do przełączania między oknami lub dokumentami.  
  
> [!NOTE]
> Istnieją pewne różnice w zachowaniu między formularzami MDI i oknami interfejsu jednostronicowego (SDI) w Windows Forms. `Opacity`Właściwość nie ma wpływu na wygląd formularzy podrzędnych MDI. Ponadto metoda nie <xref:System.Windows.Forms.Form.CenterToParent%2A> wpływa na zachowanie formularzy podrzędnych MDI.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)  
 Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.  
  
 [Porady: tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)  
 Zawiera wskazówki dotyczące tworzenia jednego lub kilku okien, które działają w ramach formularza nadrzędnego MDI.  
  
 [Instrukcje: określanie elementu podrzędnego MDI Active](how-to-determine-the-active-mdi-child.md)  
 Zawiera wskazówki dotyczące weryfikowania okna podrzędnego z fokusem (i wysyłania jego zawartości do schowka).  
  
 [Instrukcje: wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)  
 Zawiera wskazówki dotyczące transportowania informacji do aktywnego okna podrzędnego.  
  
 [Porady: aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)  
 Oferuje wskazówki dotyczące dzielenia, kaskadowania lub rozmieszczania podrzędnych okien aplikacji MDI.
