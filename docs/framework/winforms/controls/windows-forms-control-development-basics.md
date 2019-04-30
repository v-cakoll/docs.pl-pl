---
title: Podstawowe informacje o opracowywaniu formantów formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: 21b8b08e56e8b4d48fb738b86247d3f04dc4150b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759872"
---
# <a name="windows-forms-control-development-basics"></a>Podstawowe informacje o opracowywaniu formantów formularzy systemu Windows
Formant programu Windows Forms jest klasa, która pochodzi bezpośrednio lub pośrednio z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Na poniższej liście opisano typowe scenariusze dotyczące tworzenia kontrolek formularzy Windows Forms:  
  
- Łączenie istniejących kontroluje tworzenie formantu złożonego.  
  
     Formanty złożone hermetyzują interfejs użytkownika, które mogą być ponownie używane jako formant programu. Przykład formantu złożonego jest formant, który składa się z pola tekstowego i przycisku resetowania. Projektanci wizualni oferują szeroką obsługę tworzenia złożonych kontrolek. Tworzenie kontrolki złożonej, pochodzi od <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Klasa bazowa <xref:System.Windows.Forms.UserControl> zapewnia routing klawiatury dla podrzędnych kontrolki i umożliwia formanty podrzędne do działania w formie grupy. Aby uzyskać więcej informacji, zobacz [opracowywanie złożonej kontrolki formularzy Windows](developing-a-composite-windows-forms-control.md).  
  
- Rozszerzanie istniejącej kontrolki, zgodnie z własnymi lub dodać do jego funkcji.  
  
     Przycisk koloru, którego nie można zmienić i przycisk, który ma dodatkowe właściwości, który śledzi, ile razy zostanie kliknięta to przykłady formantów rozszerzonego. Można dostosować dowolną kontrolkę Windows Forms, wynikające z niego i zastępowanie lub dodanie właściwości, metody i zdarzenia.  
  
- Tworzenie formantu, która nie ma połączyć lub rozszerzanie istniejących kontrolek.  
  
     W tym scenariuszu dziedziczyć kontroli nad klasy bazowej <xref:System.Windows.Forms.Control>. Można dodać również jak zastąpić właściwości, metod i zdarzeń klasy podstawowej. Aby rozpocząć pracę, zobacz [jak: Tworzenie kontrolki formularzy Windows proste](how-to-develop-a-simple-windows-forms-control.md).  
  
 Klasa bazowa dla kontrolek Windows Forms, <xref:System.Windows.Forms.Control>, zapewnia podstawami wymagane dla wizualizacji do wyświetlenia w aplikacji klienta Windows. <xref:System.Windows.Forms.Control> zapewnia uchwyt okna, obsługuje routing komunikatów i udostępnia zdarzenia interfejsu zdarzeń klawiatury oraz myszy, a także wiele innych użytkowników. Zapewnia zaawansowane układ i zawiera właściwości specyficzne dla wizualizacji do wyświetlenia, takie jak <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>i wiele innych. Ponadto udostępnia zabezpieczenia, wątki, pomocy technicznej i współdziałania z kontrolki ActiveX. Ponieważ tak wiele infrastruktury jest dostarczany przez klasę bazową, jest stosunkowo łatwa do opracowywania własnych kontrolek Windows Forms.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie kontrolki formularzy Windows prosty](how-to-develop-a-simple-windows-forms-control.md)
- [Opracowywanie złożonej kontrolki formularzy Windows Forms](developing-a-composite-windows-forms-control.md)
- [Instrukcje: Utwórz formant programu Windows Forms pokazującej postęp](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
