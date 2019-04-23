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
ms.openlocfilehash: 44b96218e674c754a1985f2f22a36707cd1776b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294915"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Instrukcje: udostępnianie właściwości kontrolek składowych
Noszą nazwę kontrolek, które tworzą kontrolki złożonej *formanty składników*. Te kontrolki są zwykle zgłaszane w prywatnej, a zatem nie są dostępne przez dewelopera. Jeśli chcesz udostępnić użytkownikom przyszłych właściwości tych kontrolek, należy je udostępnić użytkownikowi. Właściwość składowej formantu jest uwidaczniany przez tworzenie właściwości w kontrolce użytkownika i używanie `get` i `set` metod dostępu właściwości do efektu zmianę właściwości prywatnej składowej formantu.  
  
 Należy wziąć pod uwagę kontrolki hipotetyczny użytkownika za pomocą składników przycisk o nazwie `MyButton`. W tym przykładzie, gdy użytkownik zażąda `ConstituentButtonBackColor` właściwość, wartość przechowywana we <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` są dostarczane. Po użytkownik przypisuje wartość tej właściwości, ta wartość jest automatycznie przekazywana do <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` i `set` wykona kodu, zmieniając kolor `MyButton`.  
  
 Poniższy przykład pokazuje, jak udostępnić <xref:System.Windows.Forms.Control.BackColor%2A> właściwość składowe przycisku:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Aby udostępnić z właściwością kontrolki składników  
  
1. Utwórz właściwość publiczna dla kontrolki użytkownika.  
  
2. W `get` sekcji właściwości, napisz kod, który pobiera wartość właściwości, którą chcesz uwidocznić.  
  
3. W `set` sekcji właściwości, napisz kod, który przekazuje wartość właściwości do narażonych właściwość składowej formantu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
