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
ms.openlocfilehash: 0ff5b3874d9de169f4a9f1040d601173af352c06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703234"
---
# <a name="property-changed-events"></a>Zdarzenia zmiany właściwości
Jeśli chcesz, aby Twoją kontrolą w celu wysyłania powiadomień, gdy właściwość o nazwie *PropertyName* zmiany, zdefiniować określone zdarzenie o nazwie *PropertyName* `Changed` i metodę o nazwie `On` *PropertyName* `Changed` który wywołuje zdarzenie. Konwencja nazewnictwa w formularzach Windows Forms to dołączenie wyraz *zmieniono* na nazwę właściwości. Typ delegata skojarzonego zdarzenia dla zdarzenia zmiany właściwości to <xref:System.EventHandler>, a typ danych zdarzenia jest <xref:System.EventArgs>. Klasa bazowa <xref:System.Windows.Forms.Control> definiuje wiele zdarzeń zmiany właściwości, takie jak <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>i innym osobom. Aby uzyskać ogólne informacje o zdarzeniach zobacz [zdarzenia](../../../standard/events/index.md) i [zdarzenia w kontrolkach formularzy Windows Forms](events-in-windows-forms-controls.md).  
  
 Zdarzenia zmiany właściwości są przydatne, ponieważ umożliwiają one konsumentów kontrolki można dołączyć procedury obsługi zdarzeń, które odpowiadają na zmiany. Jeśli formant musi odpowiedzieć na zdarzenie zmiany właściwości, który ją wywołuje, zastąpienie, odpowiedni `On` *PropertyName* `Changed` metody zamiast dołączając delegata do zdarzenia. Formant jest zazwyczaj odpowiada na zdarzenie zmiany właściwości, aktualizując inne właściwości lub ponownego narysowania niektórych lub wszystkich powierzchnia do rysowania.  
  
 W poniższym przykładzie pokazano sposób, w jaki `FlashTrackBar` kontrolki niestandardowej odpowiada na niektóre zdarzenia zmiany właściwości, które dziedziczy <xref:System.Windows.Forms.Control>. Aby uzyskać pełny przykład zobacz [jak: Utwórz formant programu Windows Forms pokazującej postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Zdarzenia](../../../standard/events/index.md)
- [Zdarzenia w kontrolkach formularzy Windows Forms](events-in-windows-forms-controls.md)
- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
