---
title: NumericUpDown — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 3e24fa543df9028e9866d91ec60c3cf88578ac56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740803"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown — Informacje o formancie [Formularze systemu Windows]
Formant <xref:System.Windows.Forms.NumericUpDown> wygląda podobnie do kombinacji pola tekstowego i pary strzałek, które użytkownik może kliknąć, aby dostosować wartość. Kontrolka wyświetla i ustawia pojedynczą wartość liczbową z listy stałych opcji wartości liczbowych. Użytkownik może zwiększyć i zmniejszyć liczbę, klikając strzałki w górę i w dół, naciskając klawisze strzałek w górę i w dół lub wpisując liczbę w części pola tekstowego kontrolki. Kliknięcie klawisza Strzałka w górę przenosi liczbę w dół do wartości maksymalnej; Kliknięcie klawisza Strzałka w dół przenosi liczbę w kierunku minimum.  
  
 Ze względu na uniwersalną funkcję, ten formant jest oczywisty, na przykład jeśli chcesz utworzyć formant głośności dla aplikacji odtwarzacza muzycznego. Kontrolka <xref:System.Windows.Forms.NumericUpDown> jest używana w wielu aplikacjach panelu sterowania systemu Windows.  
  
## <a name="key-properties-and-methods"></a>Właściwości i metody klucza  
 Liczby wyświetlane w polu tekstowym kontrolki mogą znajdować się w różnych formatach, w tym w formacie szesnastkowym. Aby uzyskać więcej informacji, zobacz [How to: Set a format the Windows Forms NumericUpDown Control](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Właściwości klucza kontrolki są <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (wartość domyślna 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (wartość domyślna: 0) i <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (wartość domyślna 1). Właściwość <xref:System.Windows.Forms.NumericUpDown.Value%2A> ustawia bieżącą liczbę wybraną w formancie. Właściwość <xref:System.Windows.Forms.NumericUpDown.Increment%2A> ustawia kwotę, o jaką numer jest dostosowywany, gdy użytkownik kliknie strzałkę w górę lub w dół. Gdy fokus przesunie się z formantu, wszystkie wpisane dane wejściowe zostaną zweryfikowane względem minimalnej i maksymalnej wartości liczbowej. Można zwiększyć szybkość, z jaką formant przechodzi przez liczby, gdy użytkownik ciągle naciśnie strzałkę w górę lub w dół z właściwością <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>. Kluczowe metody kontrolki są <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> i <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, kontrolka](numericupdown-control-windows-forms.md)
- [Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy Windows Forms](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
