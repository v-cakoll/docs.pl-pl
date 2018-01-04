---
title: "Podstawowe informacje o opracowywaniu formantów formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcf06f4dc0d8c70ae85d5add5a2fee078238d5e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-control-development-basics"></a>Podstawowe informacje o opracowywaniu formantów formularzy systemu Windows
Formant formularzy systemu Windows jest klasą pochodną bezpośrednio lub pośrednio <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Na poniższej liście opisano typowe scenariusze związane z opracowywaniem formanty formularzy systemu Windows:  
  
-   Łączenie istniejącego kontrolki do tworzenia złożonych kontrolek.  
  
     Formanty złożone hermetyzują interfejs użytkownika, które mogą być ponownie używane jako formant. Przykładem formantu złożonego jest formant, który składa się z pola tekstowego i przycisku resetowania. Wizualnych projektantów oferuje szeroką obsługę tworzenia złożonych kontrolek. Do tworzenia złożonych kontrolek, pochodzi z <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Klasa podstawowa <xref:System.Windows.Forms.UserControl> zapewnia routing klawiatury podrzędne kontrolki i umożliwia formantów podrzędnych z działa jako grupa. Aby uzyskać więcej informacji, zobacz [opracowywanie złożonego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Rozszerzanie istniejącego formantu, aby dostosować go lub dodać do jego funkcjonalność.  
  
     Przycisk koloru, którego nie można zmienić i przycisku, który ma dodatkowe właściwości, który śledzi, ile razy zostanie kliknięta przedstawiono formanty rozszerzone. Wszystkie kontrolki formularza systemu Windows można dostosować, wynikające z niego i zastępowanie lub dodawanie właściwości, metod i zdarzeń.  
  
-   Tworzenie formantu, który nie łączyć ani rozszerzyć istniejących formantów.  
  
     W tym scenariuszu pochodzi formantu od klasy podstawowej <xref:System.Windows.Forms.Control>. Można dodać oraz jak zastąpienie właściwości, metod i zdarzeń klasy podstawowej. Aby rozpocząć, zobacz [porady: opracowywanie prostego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 Klasa podstawowa dla formantów formularzy systemu Windows, <xref:System.Windows.Forms.Control>, zapewnia żmudne procesy wymagane do wyświetlania w aplikacji systemu Windows po stronie klienta. <xref:System.Windows.Forms.Control>udostępnia uchwyt okna, obsługuje routing wiadomości i zapewnia zdarzeń myszy i klawiatury, a także wiele innych użytkowników zdarzenia interfejsu. Udostępnia zaawansowane układu i ma właściwości specyficzne dla wyświetlania, takich jak <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>i wiele innych. Ponadto zapewnia zabezpieczeń, wątki pomocy technicznej i współdziałanie z formantami ActiveX. Ponieważ duża część infrastruktury jest dostarczany przez klasę podstawową, jest stosunkowo łatwa do opracowywania własnych formanty formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: opracowywanie prostej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Opracowywanie złożonej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Instrukcje: tworzenie kontrolki formularzy Windows Forms pokazującej postęp](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
