---
title: Obsługa danych wejściowych użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934095"
---
# <a name="handling-user-input"></a>Obsługa danych wejściowych użytkownika
W tym temacie opisano główne zdarzenia klawiatury i myszy udostępniane przez <xref:System.Windows.Forms.Control?displayProperty=nameWithType>program. Podczas obsługi zdarzenia, autorzy kontroli powinny zastąpić `On`metodę *EventName* , zamiast dołączać delegata do zdarzenia. Aby zapoznać się z przeglądem zdarzeń, zobacz Wywoływanie [zdarzeń ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
> [!NOTE]
> Jeśli żadne dane nie są skojarzone ze zdarzeniem, wystąpienie klasy <xref:System.EventArgs> bazowej jest przesyłane jako argument `On`do metody *EventName* .  
  
## <a name="keyboard-events"></a>Zdarzenia klawiatury  
 Typowe zdarzenia klawiatury, które może obsłużyć formant <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>to, <xref:System.Windows.Forms.Control.KeyUp>i.  
  
|Nazwa zdarzenia|Metoda przesłonięcia|Opis zdarzenia|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Uruchamiany tylko po pierwszym naciśnięciu klawisza.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Uruchamiany przy każdym naciśnięciu klawisza. Jeśli klucz jest wyłączony, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie jest zgłaszane według częstotliwości powtarzania zdefiniowanej przez system operacyjny.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Uruchamiany po wydaniu klucza.|  
  
> [!NOTE]
> Obsługa wprowadzania z klawiatury jest znacznie bardziej skomplikowane niż Przesłanianie zdarzeń w powyższej tabeli i wykracza poza zakres tego tematu. Aby uzyskać więcej informacji, zobacz [dane wejściowe użytkownika w Windows Forms](../user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Zdarzenia myszy  
 Zdarzenia myszy, które może obsłużyć formant <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>to,,,, <xref:System.Windows.Forms.Control.MouseUp>i.  
  
|Nazwa zdarzenia|Metoda przesłonięcia|Opis zdarzenia|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Uruchamiany po naciśnięciu przycisku myszy, gdy wskaźnik znajduje się nad kontrolką.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Uruchamiany, gdy wskaźnik wprowadzi pierwszy region kontrolki.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Uruchamiany, gdy wskaźnik myszy znajduje się nad kontrolką.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Uruchamiany, gdy wskaźnik opuści region kontrolki.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Uruchamiany, gdy wskaźnik zostanie przesunięty w region formantu.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Uruchamiany po udostępnieniu przycisku myszy, gdy wskaźnik znajduje się nad kontrolką lub wskaźnik opuszcza region kontrolki.|  
  
 Poniższy fragment kodu przedstawia przykład zastępowania <xref:System.Windows.Forms.Control.MouseDown> zdarzenia.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Poniższy fragment kodu przedstawia przykład zastępowania <xref:System.Windows.Forms.Control.MouseMove> zdarzenia.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Poniższy fragment kodu przedstawia przykład zastępowania <xref:System.Windows.Forms.Control.MouseUp> zdarzenia.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Aby uzyskać pełny kod źródłowy dla `FlashTrackBar` przykładu, zobacz [How to: Utwórz formant Windows Forms, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia w kontrolkach formularzy Windows Forms](events-in-windows-forms-controls.md)
- [Definiowanie zdarzenia](defining-an-event-in-windows-forms-controls.md)
- [Zdarzenia](../../../standard/events/index.md)
- [Dane użytkownika w formularzach Windows Forms](../user-input-in-windows-forms.md)
