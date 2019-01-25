---
title: 'Instrukcje: Implementowanie interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: c92406899cffa56a1001f50f89cb53303df5da39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560077"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Instrukcje: Implementowanie interfejsu INotifyPropertyChanged
Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Implementuje ten interfejs na obiektach biznesowych, które są używane w powiązanie danych formularzy Windows. Po wdrożeniu, interfejs komunikuje się kontrolki powiązane zmiany właściwości w obiekcie firmy.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Stosowanie wzorca PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)
- [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
- [Instrukcje: Wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
