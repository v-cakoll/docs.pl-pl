---
title: 'Instrukcje: Obsługa wprowadzania z klawiatury na poziomie formularza'
description: Dowiedz się, jak obsłużyć dane wejściowe z klawiatury dla Windows Forms na poziomie formularza, zanim komunikaty docierają do kontrolki.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904159"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Instrukcje: Obsługa wprowadzania z klawiatury na poziomie formularza
Windows Forms zapewnia możliwość obsługi komunikatów klawiatury na poziomie formularza, zanim komunikaty docierają do formantu. W tym temacie pokazano, jak wykonać to zadanie.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Aby obsłużyć komunikat klawiatury na poziomie formularza  
  
- Obsłuż <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> zdarzenie lub formularz uruchamiania, a następnie ustaw <xref:System.Windows.Forms.Form.KeyPreview%2A> Właściwość formularza na tak, aby `true` komunikaty klawiatury były odbierane przez formularz przed osiągnięciem jakichkolwiek kontrolek w formularzu. Poniższy przykład kodu obsługuje <xref:System.Windows.Forms.Control.KeyPress> zdarzenie przez wykrycie wszystkich kluczy liczbowych i zużywanie "1", "4" i "7".  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu to cała aplikacja dla powyższego przykładu. Aplikacja zawiera a <xref:System.Windows.Forms.TextBox> wraz z kilkoma innymi kontrolkami, które umożliwiają przeniesienie fokusu z <xref:System.Windows.Forms.TextBox> . W <xref:System.Windows.Forms.Control.KeyPress> przypadku użycia wartości " <xref:System.Windows.Forms.Form> 1", "4" i "7" oraz <xref:System.Windows.Forms.Control.KeyPress> zdarzenia <xref:System.Windows.Forms.TextBox> "2", "5" i "8" podczas wyświetlania pozostałych kluczy. Porównaj <xref:System.Windows.Forms.MessageBox> dane wyjściowe po naciśnięciu klawisza liczbowego, gdy <xref:System.Windows.Forms.TextBox> ma fokus z <xref:System.Windows.Forms.MessageBox> danymi wyjściowymi po naciśnięciu klawisza liczbowego, gdy fokus jest ustawiony na jednej z innych kontrolek.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzanie z klawiatury w aplikacjach formularzy systemu Windows](keyboard-input-in-a-windows-forms-application.md)
