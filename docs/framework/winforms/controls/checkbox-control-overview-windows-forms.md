---
title: "CheckBox — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a154a3f639102e3f3e2acd62626379e12bbd1344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.CheckBox> formant wskazuje, czy określony warunek jest on lub off. Zwykle jest używana do prezentowania tak/nie lub PRAWDA/FAŁSZ wybór dla użytkownika. Formanty pól wyboru w grupach służy do wyświetlania wiele wyborów, z których użytkownik może wybrać co najmniej jeden.  
  
 Kontrolka pola wyboru jest podobny do kontrolkę przycisku radiowego, w tym każdego służy do wskazywania wyboru, które zostało utworzone przez użytkownika. Są one różne, w których można wybrać przycisk radiowy tylko jednej grupy naraz. Za pomocą formantu pole wyboru jednak dowolną liczbę pól wyboru można zaznaczyć.  
  
 Pole wyboru może być połączone elementy w bazie danych przy użyciu proste powiązanie danych. Wiele pól wyboru mogą być zgrupowane za pomocą <xref:System.Windows.Forms.GroupBox> formantu. Jest to przydatne do wyglądu i również projektu interfejsu użytkownika, ponieważ grupowanych formanty mogą być przenoszone między razem na projektanta formularza. Aby uzyskać więcej informacji, zobacz [wiązanie danych formularzy systemu Windows](../../../../docs/framework/winforms/windows-forms-data-binding.md) i [GroupBox — formant](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> Formant ma dwie ważne właściwości <xref:System.Windows.Forms.CheckBox.Checked%2A> i <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość zwraca albo `true` lub `false`. <xref:System.Windows.Forms.CheckBox.CheckState%2A> Właściwość zwraca albo <xref:System.Windows.Forms.CheckState.Checked> lub <xref:System.Windows.Forms.CheckState.Unchecked>; lub, jeśli <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> może też zwracać <xref:System.Windows.Forms.CheckState.Indeterminate>. W stanie nieokreślonym pole zostanie wyświetlony z wygaszone wyglądu, aby wskazać, że ta opcja jest niedostępna.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.CheckBox>  
 [Porady: Ustawianie opcji za pomocą formularzy systemu Windows formantów CheckBox](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [Porady: odpowiadanie na formularzach systemu Windows kliknięcia elementu CheckBox](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox — formant](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
