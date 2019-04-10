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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213028"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Instrukcje: Stosowanie wzorca PropertyNameChanged
Poniższy przykład kodu demonstruje sposób stosowania *PropertyName*wzorzec zmieniono formant niestandardowy. Zastosowanie tego wzorca, gdy implementują niestandardowe formanty, które są używane z aparatem powiązanie danych formularzy Windows.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować w poprzednim przykładzie kodu:  
  
-   Wklej kod do pliku kodu puste. Należy użyć niestandardowego formantu w formularzu Windows, który zawiera `Main` metody.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementowanie interfejsu INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows](change-notification-in-windows-forms-data-binding.md)
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
