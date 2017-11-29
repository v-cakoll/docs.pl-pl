---
title: "Porady: wyświetlanie pomocy podręcznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5f57e0a7981e8cae93960c8ffc3ed2168594cf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-pop-up-help"></a>Porady: wyświetlanie pomocy podręcznej
Jednym ze sposobów Wyświetla Pomoc w formularzach systemu Windows odbywa się za pośrednictwem **pomocy** przycisk znajdujący się po prawej stronie paska tytułu dostępny za pośrednictwem <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości. Ten typ wyświetlania Pomocy jest dobrze nadaje się do użytku z okien dialogowych. Okna dialogowe wyświetlane w trybie modalnym (z <xref:System.Windows.Forms.Form.ShowDialog%2A> — metoda) ma problem otworzeniem zewnętrzna Pomoc systemów, ponieważ muszą być zamknięte przed fokus można przejść do innego okna modalne okna dialogowe. Ponadto przy użyciu **pomocy** przycisk wymóg nie **Minimalizuj** przycisk lub **Maksymalizuj** przycisku znajdującego się na pasku tytułu. Jest to standardowe okno dialogowe Konwencja, formularze zazwyczaj mają **Minimalizuj** i **Maksymalizuj** przycisków.  
  
 Należy pamiętać, że można również użyć <xref:System.Windows.Forms.HelpProvider> składnika, aby połączyć formanty do plików w systemie pomocy, nawet jeśli zaimplementowano pomoc wyskakująca. Aby uzyskać więcej informacji, zobacz [zapewnianie pomocy w aplikacji Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-pop-up-help"></a>Aby wyświetlić Pomoc wyskakująca  
  
1.  Przeciągnij [helpprovider —](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) składnika z przybornika do formularza.  
  
     Będzie ona sit na pasku w dolnej części Projektant formularzy systemu Windows.  
  
2.  W oknie właściwości ustaw <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości `true`. Spowoduje to wyświetlenie w niej przycisk ze znakiem zapytania po prawej stronie paska tytułu formularza.  
  
3.  Aby <xref:System.Windows.Forms.Form.HelpButton%2A> do wyświetlania formularza <xref:System.Windows.Forms.Form.MinimizeBox%2A> i <xref:System.Windows.Forms.Form.MaximizeBox%2A> musi mieć wartość właściwości `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> ustawioną właściwość `true`i <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość na jedną z następujących wartości: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> lub <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Wybierz kontrolkę, dla którego chcesz wyświetlić pomocy w formularzu i ustaw ciąg pomocy w oknie właściwości. Jest to ciąg tekstowy, który będzie wyświetlany w oknie podobny do [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).  
  
5.  Naciśnij klawisz **F5**.  
  
6.  Naciśnij klawisz **pomocy** znajdującego się na pasku tytułu, a następnie kliknij przycisk kontrolki, w którym można ustawić ciąg pomocy.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc w kontroli używanie etykietek narzędzi](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrowanie pomocy użytkownika w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Formularze systemu Windows](../../../../docs/framework/winforms/index.md)
