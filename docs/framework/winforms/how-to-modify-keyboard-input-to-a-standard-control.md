---
title: 'Porady: modyfikowanie sygnału z klawiatury do kontrolki standardowej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 726444e1decb3e03989317431e1f8c4a5fc4a697
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540293"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Porady: modyfikowanie sygnału z klawiatury do kontrolki standardowej
Program Windows Forms zapewnia możliwość zużywają i modyfikowanie danych wprowadzonych z klawiatury. Korzystanie z klucza odwołuje się do obsługi klucza wewnątrz obsługi metody lub zdarzenia, dzięki czemu innych metod i zdarzeń dalsze dół kolejki wiadomości nie mają wartości klucza. Modyfikowanie klucza odwołuje się do modyfikowania wartości klucza, aby metody i obsługi zdarzeń dalsze dół kolejki wiadomości odbierać różne wartości klucza. W tym temacie przedstawiono sposób wykonywania tych zadań.  
  
### <a name="to-consume-a-key"></a>Użycie klucza  
  
-   W <xref:System.Windows.Forms.Control.KeyPress> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy do `true`.  
  
     —lub—  
  
     W <xref:System.Windows.Forms.Control.KeyDown> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> klasy do `true`.  
  
    > [!NOTE]
    >  Ustawienie <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwości w <xref:System.Windows.Forms.Control.KeyDown> program obsługi zdarzeń nie zapobiega <xref:System.Windows.Forms.Control.KeyPress> i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia z są zgłaszane dla bieżącego naciśnięcie klawisza. Użyj <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> właściwości w tym celu.  
  
     Poniższy przykład zawiera fragment `switch` instrukcji, która sprawdza <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> odebranych przez <xref:System.Windows.Forms.Control.KeyPress> obsługi zdarzeń. Ten kod zużywa "A" i "" klawiszy znaków.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Aby zmodyfikować klucz znaków  
  
-   W <xref:System.Windows.Forms.Control.KeyPress> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy wartości nowy klucz znaków.  
  
     Poniższy przykład zawiera fragment `switch` instrukcji, która modyfikuje "B" na "A" i "b", "a". Należy pamiętać, że <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> ustawiono parametr `false`, dzięki czemu nowe wartości klucza są propagowane do innych metod i zdarzeń w kolejce wiadomości.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Aby zmodyfikować klucz nieznakowe  
  
-   Zastąpienie <xref:System.Windows.Forms.Control> metody, która przetwarza komunikatów systemu Windows, wykrywanie komunikat WM_KEYDOWN lub WM_SYSKEYDOWN i ustawić <xref:System.Windows.Forms.Message.WParam%2A> właściwość <xref:System.Windows.Forms.Message> parametr <xref:System.Windows.Forms.Keys> wartość, która reprezentuje nieznakowe nowego klucza.  
  
     W poniższym przykładzie pokazano, jak zastąpić <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metody kontroli wykrywania klucze F1 za pomocą F9 i zmodyfikować wszystkie naciśnięcie klawisza F3, aby F1. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control> metody, które można zastąpić, aby przechwycić komunikaty klawiatury, zobacz [dane wejściowe użytkownika w aplikacji Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) i [sposób działania wejście klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest kompletna aplikacja przykłady kodu w poprzednich sekcjach. Aplikacja używa kontrolki niestandardowej pochodną <xref:System.Windows.Forms.TextBox> klasy do wykorzystania i modyfikowanie danych wprowadzonych z klawiatury.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Wprowadzanie przez użytkownika w aplikacjach Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [Działanie wprowadzania z klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md)
