---
title: "Dostęp do właściwości domyślnej jest niejednoznaczny między członków dziedziczonych interfejsu &#39; &lt;defaultpropertyname&gt;&#39; interfejs &#39;&lt; interfacename1&gt;&#39; i &#39;&lt; defaultpropertyname&gt;&#39; interfejs &#39;&lt; interfacename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23d613668ee2d92484117759dd614ed2cad4bcb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Dostęp do właściwości domyślnej jest niejednoznaczny między członków dziedziczonych interfejsu &#39; &lt;defaultpropertyname&gt;&#39; interfejs &#39;&lt; interfacename1&gt;&#39; i &#39;&lt; defaultpropertyname&gt;&#39; interfejs &#39;&lt; interfacename2&gt;&#39;
Interfejs dziedziczy dwa interfejsy, z których każdy deklaruje domyślna właściwość o tej samej nazwie. Kompilator nie można rozpoznać dostęp do tej właściwości domyślnej bez kwalifikacji. Ilustruje to poniższy przykład.  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 Po określeniu `testObj(1)`, kompilator próbuje rozpoznać ona domyślnej właściwości. Istnieją dwa możliwe domyślnych właściwości z powodu dziedziczonych interfejsach, dlatego kompilator sygnały tego błędu.  
  
 **Identyfikator błędu:** BC30686  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Unikaj dziedziczenie żadnych elementów członkowskich o tej samej nazwie. W poprzednim przykładzie Jeśli `testObj` nie wymaga żadnego z elementów członkowskich, co oznacza, `Iface2`, Zadeklaruj ją w następujący sposób:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     —lub—  
  
-   Zaimplementuj interfejs dziedziczących w klasie. Następnie można wdrożyć wszystkich właściwości dziedziczone o różnych nazwach. Jednak tylko jeden z nich może być domyślną właściwość klasy implementującej. Ilustruje to poniższy przykład.  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
