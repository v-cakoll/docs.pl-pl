---
title: 'Porady: obsługa wprowadzania z klawiatury na poziomie formularza'
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
ms.openlocfilehash: 4913d68d7a7cced75f87d80a3bf4d099ae68b3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Porady: obsługa wprowadzania z klawiatury na poziomie formularza
Program Windows Forms zapewnia możliwość obsługi komunikatów klawiatury na poziomie formularza przed komunikaty do formantu. W tym temacie przedstawiono sposób wykonania tego zadania.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Do obsługi wiadomości klawiatury na poziomie formularza  
  
-   Obsługa <xref:System.Windows.Forms.Control.KeyPress> lub <xref:System.Windows.Forms.Control.KeyDown> zdarzeń formularz startowy i zestaw <xref:System.Windows.Forms.Form.KeyPreview%2A> właściwości formularza, aby `true` tak, aby komunikaty klawiatury są odbierane przez formularz, przed dotarciem żadnym formantem w formularzu. Poniższy kod uchwytów przykład <xref:System.Windows.Forms.Control.KeyPress> zdarzenia przez wykrycie wszystkich klawiszy numerycznych i wykorzystywanie "1", "4" i "7".  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest całej aplikacji, na przykład powyżej. Aplikacja zawiera <xref:System.Windows.Forms.TextBox> wraz z kilku formantów, które pozwalają na przenoszenie fokus z <xref:System.Windows.Forms.TextBox>. <xref:System.Windows.Forms.Control.KeyPress> Zdarzeń głównego <xref:System.Windows.Forms.Form> zużywa "1", "4" i "7" i <xref:System.Windows.Forms.Control.KeyPress> zdarzenie <xref:System.Windows.Forms.TextBox> zużywa "2", "5" i "8" podczas wyświetlania pozostałe klucze. Porównaj <xref:System.Windows.Forms.MessageBox> dane wyjściowe po naciśnięciu numer podczas klucza <xref:System.Windows.Forms.TextBox> ma fokus z <xref:System.Windows.Forms.MessageBox> output, gdy ponownie naciśniesz klawisz liczby podczas koncentruje się na jednym z innych kontrolek.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
