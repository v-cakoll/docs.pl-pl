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
ms.openlocfilehash: 19bb494d6f478c8cb7adda770f441470c4b2d19f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540369"
---
# <a name="handling-user-input"></a>Obsługa danych wejściowych użytkownika
W tym temacie opisano główne zdarzeń klawiatury oraz myszy dostarczone przez <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Podczas obsługi zdarzenia, autorzy kontrolki powinien przesłonić chronionego `On` *EventName* metody zamiast dołączając delegata do zdarzenia. Aby uzyskać przegląd zdarzeń, zobacz [Raising Events ze składnika](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Jeśli nie ma żadnych danych, skojarzone ze zdarzeniem, wystąpienie klasy bazowej <xref:System.EventArgs> jest przekazywany jako argument do `On` *EventName* metody.  
  
## <a name="keyboard-events"></a>Zdarzenia klawiatury  
 Typowe zdarzenia klawiatury, które może obsłużyć Twoją kontrolą są <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nazwa zdarzenia|Metody do przesłonięcia|Opis zdarzenia|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Wywoływane, tylko gdy naciśnięcia klawisza.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Wywoływane za każdym razem, gdy zostanie naciśnięty klawisz. Jeśli klawisz jest wciśnięty, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie jest zgłaszane w częstotliwość powtarzania zdefiniowane przez system operacyjny.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Wywoływane po zwolnieniu klawisza.|  
  
> [!NOTE]
>  Obsługa danych wprowadzonych z klawiatury jest znacznie bardziej skomplikowane niż zastępowanie zdarzenia w powyższej tabeli i wykracza poza zakres tego tematu. Aby uzyskać więcej informacji, zobacz [dane wejściowe użytkownika w formularzach Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Zdarzenia myszy  
 Zdarzenia myszy, które może obsłużyć Twoją kontrolą są <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, i <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nazwa zdarzenia|Metody do przesłonięcia|Opis zdarzenia|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Wywoływane, gdy przycisk myszy jest wciśnięty, gdy wskaźnik znajduje się nad formantem.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Wywoływane, gdy kursor po raz pierwszy najedzie z regionem danej kontrolki.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Wywoływane, gdy wskaźnik myszy nad formant.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Wywoływane po odsunięciu wskaźnika z regionem danej kontrolki.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Wywoływane, gdy wskaźnik myszy jest przesuwany w regionie formantu.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Wywoływane po zwolnieniu przycisku myszy, gdy wskaźnik znajduje się nad kontrolką lub odsunięcia kursora z regionem danej kontrolki.|  
  
 Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseDown> zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseMove> zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseUp> zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Dla pełnego kodu źródłowego dla `FlashTrackBar` przykładowe, zobacz [porady: tworzenie Windows Forms kontroli, pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Definiowanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [Dane użytkownika w formularzach Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
