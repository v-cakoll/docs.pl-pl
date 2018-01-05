---
title: 'Porady: stosowanie wzorca PropertyNameChanged'
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
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe397a92ac6e79e84757baa0c41f6e0c54b7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Porady: stosowanie wzorca PropertyNameChanged
W poniższym przykładzie kodu pokazano sposób stosowania *PropertyName*zmienione wzorzec do kontrolki niestandardowej. Podczas implementowania niestandardowych formantów, które są używane przez aparat wiązania danych formularzy systemu Windows, należy zastosować ten wzorzec.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować w poprzednim przykładzie kodu:  
  
-   Wklej kod do pliku kodu puste. Należy używać kontrolki niestandardowej w formularzu systemu Windows, który zawiera `Main` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: implementowanie interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
