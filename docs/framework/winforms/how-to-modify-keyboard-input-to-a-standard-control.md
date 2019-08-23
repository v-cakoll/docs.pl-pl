---
title: 'Instrukcje: Modyfikowanie sygnału z klawiatury do kontrolki standardowej'
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
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964290"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Instrukcje: Modyfikowanie sygnału z klawiatury do kontrolki standardowej
Windows Forms zapewnia możliwość użycia i modyfikacji danych wejściowych z klawiatury. Korzystanie z klucza odnosi się do obsługi klucza w metodzie lub obsłudze zdarzeń, tak aby inne metody i zdarzenia w dalszej kolejce kolejki komunikatów nie otrzymywały wartości klucza. Modyfikacja klucza polega na zmodyfikowaniu wartości klucza, aby metody i programy obsługi zdarzeń w dalszej części kolejki komunikatów miały inną wartość klucza. W tym temacie pokazano, jak wykonać te zadania.  
  
### <a name="to-consume-a-key"></a>Aby użyć klucza  
  
- W programie obsługi <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyPressEventArgs> zdarzeń ustaw właściwość klasy na `true`. <xref:System.Windows.Forms.Control.KeyPress>  
  
     —lub—  
  
     W programie obsługi <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyEventArgs> zdarzeń ustaw właściwość klasy na `true`. <xref:System.Windows.Forms.Control.KeyDown>  
  
    > [!NOTE]
    > Ustawienie właściwości w programie<xref:System.Windows.Forms.Control.KeyPress> obsługi <xref:System.Windows.Forms.Control.KeyUp> zdarzeń nie zapobiega wywoływaniu zdarzeń i dla bieżącego naciśnięcia klawisza. <xref:System.Windows.Forms.Control.KeyDown> <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> W tym celu użyj właściwości.<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A>  
  
     Poniższy `switch` przykład jest fragmentem instrukcji, która analizuje <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> Właściwość <xref:System.Windows.Forms.KeyPressEventArgs> odebraną przez <xref:System.Windows.Forms.Control.KeyPress> procedurę obsługi zdarzeń. Ten kod wykorzystuje klucze znaku "A" i "a".  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Aby zmodyfikować klucz znaku standardowego  
  
- W programie obsługi <xref:System.Windows.Forms.KeyPressEventArgs> <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> <xref:System.Windows.Forms.Control.KeyPress> zdarzeń ustaw właściwość klasy na wartość nowego klucza znaku.  
  
     Poniższy przykład jest fragmentem `switch` instrukcji, która modyfikuje wartość "B" na "a" i "B" na "a". Należy pamiętać, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> że właściwość <xref:System.Windows.Forms.KeyPressEventArgs> parametru jest ustawiona na `false`, więc nowa wartość klucza jest propagowana do innych metod i zdarzeń w kolejce komunikatów.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Aby zmodyfikować klucz nieznakowy  
  
- Zastąp <xref:System.Windows.Forms.Message.WParam%2A> <xref:System.Windows.Forms.Message> <xref:System.Windows.Forms.Keys> metodę, która przetwarza komunikaty systemu Windows, Wykryj komunikat przetłumaczyła lub WM_SYSKEYDOWN, a następnie ustaw właściwość parametru na wartość reprezentującą nowy klucz nieznakowy. <xref:System.Windows.Forms.Control>  
  
     Poniższy przykład kodu demonstruje, jak zastąpić metodę kontrolki, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> aby wykryć klucze F1 przez F9 i zmodyfikować dowolny klawisz F3, naciskając klawisz F1. Aby uzyskać więcej informacji <xref:System.Windows.Forms.Control> na temat metod, które można przesłonić w celu przechwycenia komunikatów klawiatury, zobacz [dane wejściowe użytkownika w aplikacji Windows Forms](user-input-in-a-windows-forms-application.md) i [sposób działania wprowadzania z klawiatury](how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest kompletną aplikacją przykładów kodu w poprzednich sekcjach. Aplikacja używa kontrolki niestandardowej pochodnej od <xref:System.Windows.Forms.TextBox> klasy, aby używać i modyfikować dane wejściowe z klawiatury.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzanie z klawiatury w aplikacjach Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Wprowadzanie przez użytkownika w aplikacjach Windows Forms](user-input-in-a-windows-forms-application.md)
- [Działanie wprowadzania z klawiatury](how-keyboard-input-works.md)
