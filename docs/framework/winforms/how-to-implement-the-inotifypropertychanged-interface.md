---
title: 'Instrukcje: Implementowanie interfejsu INotifyPropertyChanged'
description: Dowiedz się, jak zaimplementować interfejs INotifyPropertyChanged na obiektach firmowych używanych w ramach powiązania danych Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619271"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Instrukcje: Implementowanie interfejsu INotifyPropertyChanged
Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Zaimplementuj ten interfejs w obiektach firmowych, które są używane w ramach powiązania danych Windows Forms. Po zaimplementowaniu interfejs komunikuje się z kontrolką powiązaną ze zmianą właściwości w obiekcie biznesowym.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Stosowanie wzorca PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
- [Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows](change-notification-in-windows-forms-data-binding.md)
