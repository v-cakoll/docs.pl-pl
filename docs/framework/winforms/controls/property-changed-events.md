---
title: Zdarzenia zmiany właściwości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105772"
---
# <a name="property-changed-events"></a>Zdarzenia zmiany właściwości
Jeśli chcesz, aby Twoją kontrolą w celu wysyłania powiadomień, gdy właściwość o nazwie *PropertyName* zmiany, zdefiniować określone zdarzenie o nazwie *PropertyName* `Changed` i metodę o nazwie `On` *PropertyName* `Changed` który wywołuje zdarzenie. Konwencja nazewnictwa w formularzach Windows Forms to dołączenie wyraz *zmieniono* na nazwę właściwości. Typ delegata skojarzonego zdarzenia dla zdarzenia zmiany właściwości to <xref:System.EventHandler>, a typ danych zdarzenia jest <xref:System.EventArgs>. Klasa bazowa <xref:System.Windows.Forms.Control> definiuje wiele zdarzeń zmiany właściwości, takie jak <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>i innym osobom. Aby uzyskać ogólne informacje o zdarzeniach zobacz [zdarzenia](../../../standard/events/index.md) i [zdarzenia w kontrolkach formularzy Windows Forms](events-in-windows-forms-controls.md).  
  
 Zdarzenia zmiany właściwości są przydatne, ponieważ umożliwiają one konsumentów kontrolki można dołączyć procedury obsługi zdarzeń, które odpowiadają na zmiany. Jeśli formant musi odpowiedzieć na zdarzenie zmiany właściwości, który ją wywołuje, zastąpienie, odpowiedni `On` *PropertyName* `Changed` metody zamiast dołączając delegata do zdarzenia. Formant jest zazwyczaj odpowiada na zdarzenie zmiany właściwości, aktualizując inne właściwości lub ponownego narysowania niektórych lub wszystkich powierzchnia do rysowania.  
  
 W poniższym przykładzie pokazano sposób, w jaki `FlashTrackBar` kontrolki niestandardowej odpowiada na niektóre zdarzenia zmiany właściwości, które dziedziczy <xref:System.Windows.Forms.Control>. Aby uzyskać pełny przykład zobacz [jak: Utwórz formant programu Windows Forms pokazującej postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../../standard/events/index.md)
- [Zdarzenia w formantach formularzy systemu Windows](events-in-windows-forms-controls.md)
- [Właściwości formantów formularzy systemu Windows](properties-in-windows-forms-controls.md)
