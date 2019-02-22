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
ms.openlocfilehash: 58fdea3df3d82aa9f36244a11c6d353019c7ac49
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665020"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Instrukcje: Określanie, który klawisz modyfikujący został naciśnięty
Gdy tworzysz aplikację, która akceptuje naciśnięcia klawiszy przez użytkownika, można również monitorować klawisze modyfikujące, takie jak klawiszy SHIFT, ALT i CTRL. Po naciśnięciu klawisza modyfikującego w połączeniu z innych kluczy lub za pomocą kliknięć myszą, aplikacja może reagować odpowiednio. Na przykład jeśli jest wciśnięty literę S, po prostu może to spowodować "s" była wyświetlana na ekranie, ale jeśli naciskania klawiszy CTRL + S, mogą zostać zapisane bieżącego dokumentu. Jeśli możesz obsługiwać <xref:System.Windows.Forms.Control.KeyDown> zdarzenia <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> odebrane przez zdarzenie kod obsługi wyjątku określa są naciśnięte klawisze modyfikujące, które. Alternatywnie <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> określa znak, który został naciśnięty również wszelkie klawisze modyfikujące w połączeniu z bitowe OR. Jednak jeśli obsługujesz <xref:System.Windows.Forms.Control.KeyPress> zdarzenia lub zdarzenia myszy, program obsługi zdarzeń nie otrzymuje tych informacji. W takim przypadku należy użyć <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwość <xref:System.Windows.Forms.Control> klasy. W obu przypadkach należy wykonać bitowe AND odpowiednie <xref:System.Windows.Forms.Keys> wartości i wartości, które testujesz. <xref:System.Windows.Forms.Keys> Wyliczenie oferuje odmiany każdego klawisz modyfikujący, więc jest ważne, aby przeprowadzić operatora testu koniunkcji i przy użyciu poprawnej wartości. Na przykład klawisz SHIFT jest reprezentowany przez <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> i <xref:System.Windows.Forms.Keys.LShiftKey> poprawnej wartości, aby przetestować SHIFT, ponieważ klawisz modyfikujący <xref:System.Windows.Forms.Keys.Shift>. Podobnie, aby klawisz CTRL i ALT jako modyfikatory można przetestować używać <xref:System.Windows.Forms.Keys.Control> i <xref:System.Windows.Forms.Keys.Alt> wartości, odpowiednio.  
  
> [!NOTE]
>  W programowaniu w języku Visual Basic mogą też uzyskiwać dostęp informacje o kluczu za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> właściwości  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Aby ustalić, który klawisz modyfikujący został naciśnięty  
  
-   Użyj operatora testu koniunkcji `AND` operator <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwości i wartości <xref:System.Windows.Forms.Keys> wyliczeniu, aby ustalić, czy jest wciśnięty klawisz modyfikujący określonej. Poniższy przykład kodu pokazuje, jak ustalić, czy w ramach zostanie naciśnięty klawisz SHIFT <xref:System.Windows.Forms.Control.KeyPress> programu obsługi zdarzeń.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
- [Instrukcje: Określić, że jeśli Caps Lock jest włączony w języku Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
