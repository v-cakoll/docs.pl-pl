---
title: 'Instrukcje: udostępnianie właściwości kontrolek składowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015876"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Instrukcje: udostępnianie właściwości kontrolek składowych
Kontrolki wchodzące w skład formantu złożonego są nazywane *kontrolkami elementów*. Te kontrolki są zwykle zadeklarowane jako prywatne i w tym przypadku nie są dostępne dla deweloperów. Jeśli chcesz, aby właściwości tych kontrolek były dostępne dla przyszłych użytkowników, musisz uwidocznić je użytkownikowi. Właściwość kontrolki elementu jest uwidaczniana przez utworzenie właściwości w kontrolce użytkownika i użycie `get` metod i `set` dostępu tej właściwości, aby zmienić właściwość prywatną kontrolki elementu.

 Rozważmy hipotetyczny formant użytkownika z przyciskiem składnika o `MyButton`nazwie. W tym przykładzie, gdy użytkownik zażąda `ConstituentButtonBackColor` właściwości, `MyButton` zostanie wykazana wartość przechowywana <xref:System.Windows.Forms.Control.BackColor%2A> we właściwości. Gdy użytkownik przypisuje wartość do tej właściwości, ta wartość jest <xref:System.Windows.Forms.Control.BackColor%2A> automatycznie przenoszona do `MyButton` właściwości, a `set` `MyButton`kod zostanie wykonany, zmieniając kolor.

 Poniższy przykład pokazuje, <xref:System.Windows.Forms.Control.BackColor%2A> jak uwidocznić właściwość przycisku składnik:

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a>Aby uwidocznić właściwość formantu składnika

1. Utwórz Właściwość publiczną dla kontrolki użytkownika.

2. `get` W sekcji Właściwości Napisz kod, który pobiera wartość właściwości, którą chcesz uwidocznić.

3. `set` W sekcji Właściwości Napisz kod, który przekazuje wartość właściwości do właściwości uwidocznionej kontrolki składnik.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
