---
title: 'Instrukcje: Stosowanie wzorca PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 82856405ab3c9581b398f358e5bf9ecf989ce193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539769"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Instrukcje: Stosowanie wzorca PropertyNameChanged
Poniższy przykład kodu demonstruje sposób stosowania *PropertyName*wzorzec zmieniono formant niestandardowy. Zastosowanie tego wzorca, gdy implementują niestandardowe formanty, które są używane z aparatem powiązanie danych formularzy Windows.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować w poprzednim przykładzie kodu:  
  
-   Wklej kod do pliku kodu puste. Należy użyć niestandardowego formantu w formularzu Windows, który zawiera `Main` metody.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Implementowanie interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
