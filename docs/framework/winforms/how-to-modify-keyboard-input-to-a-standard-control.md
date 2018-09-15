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
ms.openlocfilehash: c109615b9a0eb61d18f7f44e3248d2b24934ee5f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625883"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Porady: modyfikowanie sygnału z klawiatury do kontrolki standardowej
Windows Forms zapewnia możliwość korzystania i modyfikowanie danych wprowadzonych z klawiatury. Korzystanie z klucza odwołuje się do obsługi klucza w ramach metody lub procedury obsługi zdarzeń, tak, aby inne metody i zdarzenia dalszych szczegółów kolejka komunikatów nie mają wartości klucza. Zmodyfikowanie klucza odwołuje się do modyfikowania wartości klucza, tak aby metody i procedury obsługi zdarzeń dalszych szczegółów kolejki komunikatów odbierać różne wartości klucza. W tym temacie przedstawiono sposób wykonywania tych zadań.  
  
### <a name="to-consume-a-key"></a>Korzystanie z klucza  
  
-   W <xref:System.Windows.Forms.Control.KeyPress> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy `true`.  
  
     —lub—  
  
     W <xref:System.Windows.Forms.Control.KeyDown> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> klasy `true`.  
  
    > [!NOTE]
    >  Ustawienie <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.Control.KeyDown> program obsługi zdarzeń nie uniemożliwia <xref:System.Windows.Forms.Control.KeyPress> i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia są zgłaszane dla bieżącego naciśnięcia klawisza. Użyj <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> właściwości w tym celu.  
  
     Poniższy przykład to fragment `switch` instrukcję, która sprawdza, czy <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> odebranych przez <xref:System.Windows.Forms.Control.KeyPress> programu obsługi zdarzeń. Ten kod wykorzystuje "A" i "" klawiszy znaków.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Aby zmodyfikować klucz znaków standardowych  
  
-   W <xref:System.Windows.Forms.Control.KeyPress> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy wartość nowy klucz znaków.  
  
     Poniższy przykład to fragment `switch` instrukcji, która modyfikuje "B", "A" i "b", "a". Należy pamiętać, że <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> parametr ma wartość `false`, dzięki czemu nowe wartości klucza są propagowane do innych metod i zdarzeń w kolejce komunikatów.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Aby zmodyfikować nieznakowe klucz  
  
-   Zastąpienie <xref:System.Windows.Forms.Control> metody, która przetwarza wiadomości Windows wykrywanie przetłumaczyła lub WM_SYSKEYDOWN wiadomości i ustawić <xref:System.Windows.Forms.Message.WParam%2A> właściwość <xref:System.Windows.Forms.Message> parametr <xref:System.Windows.Forms.Keys> wartość, która reprezentuje nowy klucz nieznakowe.  
  
     Poniższy przykład kodu demonstruje sposób zastąpienia <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metodę formantu do wykrywania klucze F1, za pomocą F9 i zmodyfikować wszelkie F3 naciśnięcie klawisza F1 — do. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control> metod, które można przesłonić, aby przechwycić komunikaty klawiatury, zobacz [dane wejściowe użytkownika w aplikacji Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) i [sposób działania wejście klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest kompletnej aplikacji, aby uzyskać przykłady kodu w poprzedniej sekcji. Aplikacja korzysta z kontrolki niestandardowej, która jest pochodną <xref:System.Windows.Forms.TextBox> klasy w celu umożliwienia użycia i modyfikowanie danych wprowadzonych z klawiatury.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie z klawiatury w aplikacjach Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Wprowadzanie przez użytkownika w aplikacjach Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [Działanie wprowadzania z klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md)
