---
title: 'Instrukcje: Implementowanie interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 51c0b1fa535921b7b33a16f55bdc8b76d6125e72
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704092"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Instrukcje: Implementowanie interfejsu INotifyPropertyChanged
Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Implementuje ten interfejs na obiektach biznesowych, które są używane w powiązanie danych formularzy Windows. Po wdrożeniu, interfejs komunikuje się kontrolki powiązane zmiany właściwości w obiekcie firmy.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Stosowanie wzorca PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
- [Instrukcje: Wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)
