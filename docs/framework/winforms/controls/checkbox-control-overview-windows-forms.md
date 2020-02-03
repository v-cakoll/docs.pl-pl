---
title: CheckBox — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737096"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.CheckBox> Windows Forms wskazuje, czy określony warunek jest włączony, czy wyłączony. Jest on często używany do prezentowania użytkownikowi wyboru opcji tak/nie lub prawda/fałsz. Możesz użyć kontrolek pola wyboru w grupach, aby wyświetlić wiele opcji, z których użytkownik może wybrać jeden lub więcej.  
  
 Kontrolka pole wyboru jest podobna do kontrolki przycisk radiowy, w której każdy jest używany do wskazania wyboru dokonanego przez użytkownika. Różnią się one tylko jednym przyciskiem radiowym w grupie. Za pomocą kontrolki pole wyboru można wybrać dowolną liczbę pól wyboru.  
  
 Pole wyboru może być połączone z elementami w bazie danych przy użyciu prostego powiązania danych. Wiele pól wyboru można grupować przy użyciu kontrolki <xref:System.Windows.Forms.GroupBox>. Jest to przydatne w przypadku wyglądu wizualizacji, a także dla projektowania interfejsu użytkownika, ponieważ pogrupowane kontrolki można przenosić razem z projektantem formularzy. Aby uzyskać więcej informacji, zobacz [Windows Forms powiązania danych](../windows-forms-data-binding.md) i [kontrolki grupy](groupbox-control-windows-forms.md).  
  
 Kontrolka <xref:System.Windows.Forms.CheckBox> ma dwie ważne właściwości, <xref:System.Windows.Forms.CheckBox.Checked%2A> i <xref:System.Windows.Forms.CheckBox.CheckState%2A>. Właściwość <xref:System.Windows.Forms.CheckBox.Checked%2A> zwraca `true` lub `false`. Właściwość <xref:System.Windows.Forms.CheckBox.CheckState%2A> zwraca <xref:System.Windows.Forms.CheckState.Checked> lub <xref:System.Windows.Forms.CheckState.Unchecked>; lub, jeśli właściwość <xref:System.Windows.Forms.CheckBox.ThreeState%2A> jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> może również zwrócić <xref:System.Windows.Forms.CheckState.Indeterminate>. W nieokreślonym stanie pole jest wyświetlane z wygaszonym wyglądem, aby wskazać, że opcja jest niedostępna.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.CheckBox>
- [Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Instrukcje: odpowiadanie na kliknięcia kontrolki CheckBox formularzy Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox, kontrolka](checkbox-control-windows-forms.md)
