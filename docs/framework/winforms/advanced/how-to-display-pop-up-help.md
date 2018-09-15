---
title: 'Porady: wyświetlanie pomocy podręcznej'
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
ms.openlocfilehash: 47833e734c09e402ab1824b9c629b2ba39acfb9f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658694"
---
# <a name="how-to-display-pop-up-help"></a>Porady: wyświetlanie pomocy podręcznej
Jest jednym ze sposobów, aby wyświetlić Pomoc na formularzach Windows Forms **pomocy** przycisk znajdujący się po prawej stronie paska tytułu, dostępne za pośrednictwem <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości. Ten typ ekranu Pomocy jest dobrze nadaje się do użytku z okien dialogowych. Okna dialogowe wyświetlane w trybie modalnym (przy użyciu <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda) mają problemy z wyświetlania zewnętrzna Pomoc systemów, ponieważ modalnych okien dialogowych, które muszą zostać zamknięte przed fokus można przejść do innego okna. Ponadto za pomocą **pomocy** przycisk wymaga, że istnieje nie **Minimalizuj** przycisk lub **Maksymalizuj** przycisk na pasku tytułu. To Konwencji standardowe okno dialogowe, formularze, zwykle mają **Minimalizuj** i **Maksymalizuj** przycisków.  
  
 Należy pamiętać, że można również użyć <xref:System.Windows.Forms.HelpProvider> składnika formanty łączy do plików w systemie pomocy, nawet jeśli udało Ci się wdrożyć Pomoc podręczną. Aby uzyskać więcej informacji, zobacz [zapewnianie pomocy w aplikacji Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-display-pop-up-help"></a>Aby Wyświetlanie pomocy podręcznej  
  
1.  Przeciągnij [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) składnika z przybornika do formularza.  
  
     Będzie ona znajdują się w pasku w dolnej części projektanta Windows Forms.  
  
2.  W oknie właściwości ustaw <xref:System.Windows.Forms.Form.HelpButton%2A> właściwość `true`. Spowoduje to wyświetlenie w niej przycisk ze znakiem zapytania po prawej stronie paska tytułu formularza.  
  
3.  Aby <xref:System.Windows.Forms.Form.HelpButton%2A> do wyświetlania formularza <xref:System.Windows.Forms.Form.MinimizeBox%2A> i <xref:System.Windows.Forms.Form.MaximizeBox%2A> właściwości musi być równa `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> właściwością `true`i <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość na jedną z następujących wartości: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> lub <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Wybierz kontrolkę, dla którego chcesz wyświetlić pomocy w formularzu i ustaw ciąg pomocy w oknie dialogowym właściwości. Jest to ciąg tekstowy, który będzie wyświetlany w oknie podobne do [etykietki narzędzia](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).  
  
5.  Naciśnij klawisz **F5**.  
  
6.  Naciśnij klawisz **pomocy** znajdujący się na pasku tytułu, a następnie kliknij przycisk kontrolki, na którym można ustawić parametrów pomocy.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc do kontrolek przy użyciu etykietek narzędzi](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrowanie pomocy użytkownika z formularzami Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
