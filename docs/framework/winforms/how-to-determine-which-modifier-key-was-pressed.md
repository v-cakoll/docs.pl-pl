---
title: 'Instrukcje: Określanie, który klawisz modyfikujący został naciśnięty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964314"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Instrukcje: Określanie, który klawisz modyfikujący został naciśnięty
Podczas tworzenia aplikacji, która akceptuje naciśnięcia klawiszy użytkownika, może być również konieczne monitorowanie klawiszy modyfikujących, takich jak klawisze SHIFT, ALT i CTRL. Gdy klawisz modyfikujący zostanie wciśnięty w połączeniu z innymi kluczami lub kliknięciem myszy, aplikacja może odpowiednio reagować. Na przykład po naciśnięciu litery S może to spowodować, że "S" pojawi się na ekranie, ale po naciśnięciu klawiszy CTRL + S bieżący dokument może zostać zapisany. W przypadku obsługi <xref:System.Windows.Forms.Control.KeyDown> zdarzenia <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Właściwość <xref:System.Windows.Forms.KeyEventArgs> odebrana przez procedurę obsługi zdarzeń określa, które klawisze modyfikujące zostały naciśnięte. <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> Alternatywnie<xref:System.Windows.Forms.KeyEventArgs> Właściwość określa znak, który został naciśnięty, a także wszystkie klawisze modyfikujące z bitowym lub. Jednak w przypadku obsługi <xref:System.Windows.Forms.Control.KeyPress> zdarzenia lub zdarzenia myszy program obsługi zdarzeń nie otrzymuje tych informacji. W takim przypadku należy użyć <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwości <xref:System.Windows.Forms.Control> klasy. W obu przypadkach należy wykonać bitowe i odpowiednią <xref:System.Windows.Forms.Keys> wartość oraz wartość, którą testujesz. <xref:System.Windows.Forms.Keys> Wyliczenie oferuje różne odmiany poszczególnych klawiszy modyfikujących, dlatego ważne jest, aby wykonać bitowe i z poprawną wartością. Na przykład klawisz Shift jest reprezentowany przez <xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>i <xref:System.Windows.Forms.Keys.LShiftKey> poprawna wartość w celu przetestowania klawisza modyfikującego jest <xref:System.Windows.Forms.Keys.Shift>równa. Podobnie, aby testować pod kątem kombinacji klawiszy CTRL i Alt jako modyfikatorów <xref:System.Windows.Forms.Keys.Control> , <xref:System.Windows.Forms.Keys.Alt> należy odpowiednio użyć wartości i.  
  
> [!NOTE]
> Visual Basic programiści mogą również uzyskać dostęp do kluczowych informacji <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> za pomocą właściwości  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Aby określić, który klawisz modyfikujący został naciśnięty  
  
- Użyj operatora bitowego `AND` <xref:System.Windows.Forms.Control.ModifierKeys%2A> z właściwością <xref:System.Windows.Forms.Keys> i wartością wyliczenia, aby określić, czy określony klawisz modyfikujący został naciśnięty. Poniższy przykład kodu pokazuje, jak ustalić, czy klawisz Shift jest wciśnięty w ramach <xref:System.Windows.Forms.Control.KeyPress> procedury obsługi zdarzeń.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Wprowadzanie z klawiatury w aplikacjach Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Instrukcje: Określ, czy CapsLock jest włączona w Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
