---
title: "Porady: określanie, który klawisz modyfikujący został naciśnięty"
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5f749d22c09d166e81ea08068f760f24960ec83
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Porady: określanie, który klawisz modyfikujący został naciśnięty
Podczas tworzenia aplikacji, która akceptuje naciśnięcia klawiszy przez użytkownika, można również monitorować klawisze modyfikujące, takie jak klawiszy SHIFT, ALT i CTRL. Po naciśnięciu klawisza modyfikator w połączeniu z kluczy lub kliknięcie myszą, aplikacja może odpowiadać odpowiednio. Na przykład jeśli litera S zostanie naciśnięty, po prostu może to spowodować "s" na ekranie, ale jeśli naciskania klawiszy CTRL + S, mogą zostać zapisane bieżącego dokumentu. Jeśli można obsługiwać <xref:System.Windows.Forms.Control.KeyDown> zdarzenia <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> odebranych przez zdarzenie obsługi Określa, które klawisze modyfikujące naciśnięciu. Alternatywnie <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> określa znak, który został naciśnięty również jako wszystkie klawisze modyfikujące, w połączeniu z bitowego OR. Jednak jeśli jest obsługa <xref:System.Windows.Forms.Control.KeyPress> zdarzenie lub zdarzenia myszy programu obsługi zdarzeń nie otrzymuje informacji. W takim przypadku należy użyć <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwość <xref:System.Windows.Forms.Control> klasy. W obu przypadkach należy wykonać iloczynu bitowego AND z odpowiednią <xref:System.Windows.Forms.Keys> wartości i wartości podczas testowania. <xref:System.Windows.Forms.Keys> Wyliczenie oferuje zmian każdego klawisz modyfikujący, dlatego należy przeprowadzić operatora testu koniunkcji i z poprawną wartość. Na przykład klawisz SHIFT jest reprezentowana przez <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> i <xref:System.Windows.Forms.Keys.LShiftKey> poprawną wartość do testowania SHIFT, ponieważ jest klawisz modyfikujący <xref:System.Windows.Forms.Keys.Shift>. Podobnie do testowania TROLERA i ALT jako modyfikatory możesz należy używać <xref:System.Windows.Forms.Keys.Control> i <xref:System.Windows.Forms.Keys.Alt> wartości odpowiednio.  
  
> [!NOTE]
>  Języka Visual Basic można również dostęp do kluczowych informacji za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> właściwości  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Aby ustalić, który klawisz modyfikujący został naciśnięty  
  
-   Użyj operatora testu koniunkcji `AND` operatora z <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwości i wartości <xref:System.Windows.Forms.Keys> wyliczeniu, aby określić, czy zostanie naciśnięty klawisz modyfikujący konkretnego. Poniższy przykład kodu pokazuje sposób określania, czy w ramach zostanie naciśnięty klawisz SHIFT <xref:System.Windows.Forms.Control.KeyPress> obsługi zdarzeń.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Porady: Określ, czy CapsLock występuje na w języku Visual Basic](http://msdn.microsoft.com/library/91e60f5c-dd61-4222-ba5f-39af803afd8c)
