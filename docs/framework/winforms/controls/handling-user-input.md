---
title: "Obsługa danych wejściowych użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c3da2c4661acdb358c38fb871de70fd470f7991
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-user-input"></a>Obsługa danych wejściowych użytkownika
W tym temacie opisano głównego zdarzenia klawiatury i myszy pochodzącymi <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Podczas obsługi zdarzenia, autorzy kontroli powinny zastępować chronionej `On` *EventName* zamiast dołączanie delegata zdarzenia. Przegląd zdarzeń, zobacz [wywoływanie zdarzeń od składnika](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Jeśli nie ma danych skojarzonych z zdarzenie wystąpienia klasy podstawowej <xref:System.EventArgs> jest przekazywany jako argument `On` *EventName* metody.  
  
## <a name="keyboard-events"></a>Zdarzenia klawiatury  
 Typowe zdarzenia klawiatury, jaką może obsłużyć spod kontroli są <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nazwa zdarzenia|Metoda zastąpienia|Opis zdarzenia|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Uruchamiany, tylko gdy naciśnięcia klawisza.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Wywoływane za każdym razem, gdy zostanie naciśnięty klawisz. Jeśli klawisz jest wciśnięty, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie jest zgłaszane w częstotliwość powtarzania zdefiniowane przez system operacyjny.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Wywoływane, gdy klawisz zostanie zwolniony.|  
  
> [!NOTE]
>  Obsługa danych wprowadzonych z klawiatury jest znacznie bardziej skomplikowane niż zastępowanie zdarzeń w powyższej tabeli i wykracza poza zakres tego tematu. Aby uzyskać więcej informacji, zobacz [dane wejściowe użytkownika w formularzach systemu Windows](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Zdarzenia myszy  
 Zdarzenia myszy, jaką może obsłużyć spod kontroli są <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, i <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nazwa zdarzenia|Metoda zastąpienia|Opis zdarzenia|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Wywoływane, gdy zostanie naciśnięty przycisk myszy, gdy wskaźnik znajduje się nad formantem.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Wywoływane, gdy wskaźnik myszy jest przesuwany najpierw region formantu.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Wywoływane, gdy wskaźnik myszy jest przesuwany nad formantem.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Wywoływane, gdy wskaźnik myszy opuści obszaru formantu.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Wywoływane, gdy wskaźnik myszy przesuwa się w regionie formantu.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Uruchamiany po zwolnieniu przycisku myszy, gdy wskaźnik myszy znajduje się nad formantem lub wskaźnik myszy opuści obszaru formantu.|  
  
 Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseDown> zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseMove> zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseUp> zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Dla kodu źródłowego pełną `FlashTrackBar` przykładowe, zobacz [jak: utworzyć Windows formularze kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Dodawanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [Dane wejściowe użytkownika w formularzach systemu Windows](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
