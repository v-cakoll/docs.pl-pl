---
title: "RadioButton — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac0a04c506919ef807a3f8c5ed5aa75ee998f64a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.RadioButton> formanty wyświetlania zestawu co najmniej dwa wzajemnie wykluczających się opcji do użytkownika. Podczas gdy przycisków radiowych i pól wyboru mogą pojawiać się działają podobnie, jest istotną różnicą:, gdy użytkownik wybierze przycisk radiowy, innych przycisków radiowych w tej samej grupy nie można również wybrać. Z kolei można wybrać dowolną liczbę pól wyboru. Definiowanie Grupa przycisków radiowych informuje użytkownika, "W tym miejscu jest zestaw opcji, z których można wybrać jeden i tylko jeden".  
  
## <a name="using-the-control"></a>Za pomocą formantu  
 Gdy <xref:System.Windows.Forms.RadioButton> formant zostanie kliknięty, jego <xref:System.Windows.Forms.RadioButton.Checked%2A> właściwość jest ustawiona na `true` i <xref:System.Windows.Forms.Control.Click> jest wywoływana procedura obsługi zdarzeń. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Zdarzenie jest zgłaszane, gdy wartość <xref:System.Windows.Forms.RadioButton.Checked%2A> zmiany właściwości. Jeśli <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> właściwość jest ustawiona na `true` (domyślnie), gdy przycisk radiowy zostanie wybrany wszystkich innych użytkowników w grupie są automatycznie wyczyszczone. Ta właściwość jest zwykle tylko ustawioną `false` stosowania kodu walidacji się upewnić się, że przycisk radiowy wybrana jest opcja dopuszczalny. Tekst wyświetlany w formancie ustawiono <xref:System.Windows.Forms.Control.Text%2A> właściwość, która może zawierać skróty klucza dostępu. Klucz dostępu umożliwia użytkownikowi "kliknij" formantu, naciskając klawisz ALT z kluczem dostępu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) i [jak: ustawić tekst wyświetlany przez formant formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> Kontroli mogą pojawiać się jak przycisk polecenia, które wydaje się być wciśnięte zaznaczenie tej opcji, jeśli <xref:System.Windows.Forms.RadioButton.Appearance%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.Appearance.Button>. Przyciski radiowe można również wyświetlanie obrazów przy użyciu <xref:System.Windows.Forms.ButtonBase.Image%2A> i <xref:System.Windows.Forms.ButtonBase.ImageList%2A> właściwości. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie obrazu wyświetlanego przez formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RadioButton>  
 [Panel — Informacje o formancie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Informacje o formancie GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Informacje o formancie CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Porady: Tworzenie klawiszy dostępu dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Porady: Ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Porady: Grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [RadioButton — formant](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
