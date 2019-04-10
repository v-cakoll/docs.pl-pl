---
title: 'Instrukcje: Implementowanie interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225602"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Instrukcje: Implementowanie interfejsu INotifyPropertyChanged
Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Implementuje ten interfejs na obiektach biznesowych, które są używane w powiązanie danych formularzy Windows. Po wdrożeniu, interfejs komunikuje się kontrolki powiązane zmiany właściwości w obiekcie firmy.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Stosowanie wzorca PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
- [Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows](change-notification-in-windows-forms-data-binding.md)
