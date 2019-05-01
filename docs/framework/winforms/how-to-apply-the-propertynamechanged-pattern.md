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
ms.openlocfilehash: 36670eee6235277a7fe98770192df9ae05d3dd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966819"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Instrukcje: Stosowanie wzorca PropertyNameChanged
Poniższy przykład kodu demonstruje sposób stosowania *PropertyName*wzorzec zmieniono formant niestandardowy. Zastosowanie tego wzorca, gdy implementują niestandardowe formanty, które są używane z aparatem powiązanie danych formularzy Windows.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować w poprzednim przykładzie kodu:  
  
- Wklej kod do pliku kodu puste. Należy użyć niestandardowego formantu w formularzu Windows, który zawiera `Main` metody.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementowanie interfejsu INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
