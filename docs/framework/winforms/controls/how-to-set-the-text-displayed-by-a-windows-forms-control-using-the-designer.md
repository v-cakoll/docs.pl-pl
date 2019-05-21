---
title: 'Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 37ab3823a41cca2eeea550c90e92e90bc364c759
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960353"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows przy użyciu narzędzia Projektant

Kontrolek formularzy Windows Forms jest zazwyczaj wyświetlane jakiś tekst, który jest powiązany z podstawową funkcją kontroli. Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle wyświetla podpis, który wskazuje, jakie działania będą wykonywane po kliknięciu przycisku. Dla wszystkich kontrolek, możesz ustawić lub zwróć tekst przy użyciu <xref:System.Windows.Forms.Control.Text%2A> właściwości. Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości.

### <a name="to-set-the-text-and-font-with-the-designer"></a>Aby ustawić tekstu i czcionek, za pomocą projektanta

1. W oknie właściwości ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości kontrolki na odpowiedni ciąg.

     Do utworzenia klawiszem skrótu podkreślony obejmuje handlowe "i" (&) przed literą, który zostanie klawisz skrótu.

2. W oknie dialogowym właściwości kliknij przycisk oznaczony wielokropkiem (![przycisk wielokropka (...) w oknie dialogowym właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok pozycji <xref:System.Windows.Forms.Control.Font%2A> właściwości.

     W oknie dialogowym standardowa czcionkę wybierz czcionkę, styl czcionki, rozmiaru, efekty (na przykład przekreślenie lub podkreślenie) i skryptów, które mają.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Używanie czcionek i tekstu](../advanced/using-fonts-and-text.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
