---
title: 'Porady: implementowanie interfejsu INotifyPropertyChanged'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Porady: implementowanie interfejsu INotifyPropertyChanged
Poniższy przykład kodu pokazuje, jak wdrożyć <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Implementuje ten interfejs w obiektach biznesowych, które są używane w wiązanie danych formularzy systemu Windows. Po zaimplementowaniu interfejsu komunikuje się powiązanej kontrolki zmiany właściwości obiektu biznesowego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: stosowanie wzorca PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Powiązanie danych formularzy systemu Windows](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Powiadomienie o zmianie w powiązaniu danych formularzy systemu Windows](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
