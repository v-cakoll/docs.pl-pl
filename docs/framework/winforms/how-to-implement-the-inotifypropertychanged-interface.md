---
title: 'Porady: implementowanie interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 8f64b51a7d56f609399baac613a651e82b91e6df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536415"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Porady: implementowanie interfejsu INotifyPropertyChanged
Poniższy przykład kodu pokazuje, jak wdrożyć <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Implementuje ten interfejs w obiektach biznesowych, które są używane w wiązanie danych formularzy systemu Windows. Po zaimplementowaniu interfejsu komunikuje się powiązanej kontrolki zmiany właściwości obiektu biznesowego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: stosowanie wzorca PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
