---
title: 'Instrukcje: Wyświetlanie pomocy podręcznej'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: bf3bcbff0cd6f3bbf71e96e748cb170d5ce68dfc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211389"
---
# <a name="how-to-display-pop-up-help"></a>Instrukcje: Wyświetlanie pomocy podręcznej

Jest jednym ze sposobów, aby wyświetlić Pomoc na formularzach Windows Forms **pomocy** przycisk znajdujący się po prawej stronie paska tytułu, dostępne za pośrednictwem <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości. Ten typ ekranu Pomocy jest dobrze nadaje się do użytku z okien dialogowych. Okna dialogowe wyświetlane w trybie modalnym (przy użyciu <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda) mają problemy z wyświetlania zewnętrzna Pomoc systemów, ponieważ modalnych okien dialogowych, które muszą zostać zamknięte przed fokus można przejść do innego okna. Ponadto za pomocą **pomocy** przycisk wymaga, że istnieje nie **Minimalizuj** przycisk lub **Maksymalizuj** przycisk na pasku tytułu. To Konwencji standardowe okno dialogowe, formularze, zwykle mają **Minimalizuj** i **Maksymalizuj** przycisków.

Można również użyć <xref:System.Windows.Forms.HelpProvider> składnika formanty łączy do plików w systemie pomocy, nawet jeśli udało Ci się wdrożyć Pomoc podręczną. Aby uzyskać więcej informacji, zobacz [zapewnianie pomocy w aplikacji Windows](how-to-provide-help-in-a-windows-application.md).

## <a name="display-pop-up-help"></a>Wyświetlanie pomocy podręcznej

1. W programie Visual Studio przeciągnij [HelpProvider](../controls/helpprovider-component-windows-forms.md) składnika z przybornika do formularza.

   Będzie ona znajdują się w pasku w dolnej części projektanta Windows Forms.

2. W oknie właściwości ustaw <xref:System.Windows.Forms.Form.HelpButton%2A> właściwość `true`. Spowoduje to wyświetlenie w niej przycisk ze znakiem zapytania po prawej stronie paska tytułu formularza.

3. Aby <xref:System.Windows.Forms.Form.HelpButton%2A> do wyświetlania formularza <xref:System.Windows.Forms.Form.MinimizeBox%2A> i <xref:System.Windows.Forms.Form.MaximizeBox%2A> właściwości musi być równa `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> właściwością `true`i <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość na jedną z następujących wartości: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> lub <xref:System.Windows.Forms.FormBorderStyle.Sizable>.

4. Wybierz kontrolkę, dla którego chcesz wyświetlić pomocy w formularzu i ustaw ciąg pomocy w oknie dialogowym właściwości. Jest to ciąg tekstowy, który będzie wyświetlany w oknie podobne do [etykietki narzędzia](../controls/tooltip-component-windows-forms.md).

5. Naciśnij klawisz **F5**.

6. Naciśnij klawisz **pomocy** znajdujący się na pasku tytułu, a następnie kliknij przycisk kontrolki, na którym można ustawić parametrów pomocy.

## <a name="see-also"></a>Zobacz także

- [Pomoc do kontrolek przy użyciu etykietek narzędzi](control-help-using-tooltips.md)
- [Integrowanie pomocy użytkownika z formularzami Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
