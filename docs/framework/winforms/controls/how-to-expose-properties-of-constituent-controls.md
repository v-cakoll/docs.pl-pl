---
title: "Porady: udostępnianie właściwości formantów składowych"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a970864a406f98477fa3e09bdefcf959d2078fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Porady: udostępnianie właściwości formantów składowych
Formanty, które tworzą formantu złożonego są nazywane *formanty składników*. Tych kontrolek zwykle są deklarowane jako prywatny, a w związku z tym nie można uzyskać dostępu do tych przez dewelopera. Jeśli chcesz udostępnić użytkownikom przyszłych właściwości tych kontrolek musi ujawniać je użytkownikowi. Właściwość formantu składników jest udostępniana przez tworzenie właściwości formantu użytkownika i używanie `get` i `set` metody dostępu właściwości dokonanie zmiany właściwości prywatnej składowych formantu.  
  
 Rozważ kontrolkę użytkownika hipotetyczny składowych przycisk o nazwie `MyButton`. W tym przykładzie, gdy użytkownik zażąda `ConstituentButtonBackColor` właściwości, do wartości przechowywanej w <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` jest dostarczany. Gdy użytkownik przypisuje wartość do tej właściwości, ta wartość jest automatycznie przekazywane do <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` i `set` kod zostanie wykonany, zmianę koloru `MyButton`.  
  
 Poniższy przykład przedstawia sposób ujawniać <xref:System.Windows.Forms.Control.BackColor%2A> właściwość przycisku składników:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Do udostępnienia właściwości formantu składników  
  
1.  Utwórz właściwość publiczna dla formantu użytkownika.  
  
2.  W `get` sekcji właściwości zapisu kod, który pobiera wartość właściwości chcesz udostępnić.  
  
3.  W `set` sekcji właściwości zapisu kod, który przekazuje wartość właściwości do ujawnionych właściwości formantu składników.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.UserControl>  
 [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
