---
title: Podstawowe informacje na temat tworzenia formantów
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: fab0a76e2f9fdb7e2f89e9d6a10dd9c522a6d8e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739917"
---
# <a name="windows-forms-control-development-basics"></a>Podstawowe informacje o opracowywaniu formantów formularzy systemu Windows
Formant Windows Forms jest klasą, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Na poniższej liście opisano typowe scenariusze tworzenia Windows Forms formantów:  
  
- Łączenie istniejących kontrolek w celu utworzenia kontrolki złożonej.  
  
     Kontrolki złożone hermetyzują interfejs użytkownika, który może być ponownie używany jako formant. Przykładem formantu złożonego jest kontrolka, która składa się z pola tekstowego i przycisku reset. Projektanci wizualizacji oferują rozbudowaną obsługę tworzenia formantów złożonych. Aby utworzyć formant złożony, należy uzyskać od <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Klasa bazowa <xref:System.Windows.Forms.UserControl> zapewnia Routing klawiatury dla formantów podrzędnych i umożliwia kontrolom podrzędnym działanie jako grupę. Aby uzyskać więcej informacji, zobacz [Tworzenie złożonego formantu Windows Forms](developing-a-composite-windows-forms-control.md).  
  
- Rozszerzanie istniejącej kontrolki w celu dostosowania jej lub dodania do jej funkcjonalności.  
  
     Przycisk, którego kolor nie może zostać zmieniony i przycisk, który ma dodatkową właściwość, która śledzi, ile razy został kliknięty, są przykładami rozszerzonych kontrolek. Możesz dostosować dowolną kontrolkę Windows Forms, wyprowadzając ją z niej i zastępując lub dodając właściwości, metody i zdarzenia.  
  
- Tworzenie kontrolki, która nie łączy ani nie rozszerzy istniejących kontrolek.  
  
     W tym scenariuszu należy utworzyć formant z klasy bazowej <xref:System.Windows.Forms.Control>. Można dodawać oraz zastępować właściwości, metody i zdarzenia klasy bazowej. Aby rozpocząć, zobacz [How to: Programowanie prostej kontrolki Windows Forms](how-to-develop-a-simple-windows-forms-control.md).  
  
 Klasa bazowa dla kontrolek Windows Forms, <xref:System.Windows.Forms.Control>, zapewnia instalację wodociągową wymaganą do wyświetlania wizualizacji w aplikacjach opartych na systemie Windows po stronie klienta. <xref:System.Windows.Forms.Control> zapewnia obsługę okna, obsługuje routing komunikatów i udostępnia zdarzenia myszy i klawiatury oraz wiele innych zdarzeń interfejsu użytkownika. Udostępnia zaawansowane układy i ma właściwości specyficzne dla wyświetlania wizualnego, takie jak <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>i wielu innych. Ponadto zapewnia zabezpieczenia, obsługę wątków i współdziałanie z kontrolkami ActiveX. Ze względu na to, że większość infrastruktury jest dostarczana przez klasę bazową, jest stosunkowo łatwa do opracowania własnych formantów Windows Forms.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: opracowywanie prostej kontrolki formularzy Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Opracowywanie złożonej kontrolki formularzy Windows Forms](developing-a-composite-windows-forms-control.md)
- [Instrukcje: tworzenie kontrolki formularzy Windows Forms pokazującej postęp](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
