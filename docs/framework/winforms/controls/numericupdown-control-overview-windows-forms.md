---
title: NumericUpDown — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 218eb685e546acac76a18450612a1601ab87276b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109879"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown — Informacje o formancie [Formularze systemu Windows]
<xref:System.Windows.Forms.NumericUpDown> Kontrolka wygląda kombinacją pole tekstowe oraz pary strzałki, które użytkownik może kliknąć, aby dopasować wartość. Wyświetla i ustawia wartość liczbową jednej z listy stałą wartością numeryczną opcji kontrolki. Użytkownik może zwiększyć i zmniejszyć liczbę, klikając pozycję w górę i w dół strzałki, naciskając klawisze strzałek w górę i w dół lub wpisując liczbę w polu tekstowym formantu. Klikając przycisk Strzałka w górę przenosi liczbę kierunku maksymalną; klikając przycisk strzałki w dół przenosi liczbę kierunku minimum.  
  
 Ze względu na jego działanie wszechstronna ten formant jest oczywistym wyborem, na przykład, chcąc tworzenia Regulacja głośności, dla aplikacji odtwarzacz muzyczny. <xref:System.Windows.Forms.NumericUpDown> Formant jest używany w wielu aplikacjach Panelu sterowania Windows.  
  
## <a name="key-properties-and-methods"></a>Kluczowe właściwości i metody  
 Liczby wyświetlane w polu tekstowym kontrolki można w różnych formatach, takich jak szesnastkowe. Aby uzyskać więcej informacji, zobacz [jak: Ustawienie formatu dla kontrolki NumericUpDown formularzy Windows Forms](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Kluczowe właściwości kontrolki są <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (wartość domyślna to 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (domyślna wartość 0), a <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (domyślna wartość 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Właściwość ustawia bieżący numer wybrana w kontrolce. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Właściwość ustawia kwotę, że liczba jest dostosowane, gdy użytkownik kliknie w górę lub Strzałka w dół. Gdy fokus znajdzie się poza formant, wszelkie dane wpisane zostanie zweryfikowana względem minimalne i maksymalne wartości liczbowe. Można zwiększyć szybkość, która kontrolka przechodzi przez cyfry, gdy użytkownik naciśnie stale w górę lub strzałkę w dół, za pomocą <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> właściwości. Metody klucza kontrolki są <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> i <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, kontrolka](numericupdown-control-windows-forms.md)
- [Instrukcje: Ustawienie formatu dla formantu NumericUpDown formularzy Windows](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
