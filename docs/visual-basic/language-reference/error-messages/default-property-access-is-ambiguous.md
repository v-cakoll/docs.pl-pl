---
title: Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego członka „<defaultpropertyname>" interfejsu „<interfacename1>" i dziedziczonego członka „<defaultpropertyname>" interfejsu „<interfacename2>"
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5f058c8e7d480b9145452ae85f186a6ac2ed0d56
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836353"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego członków\<defaultpropertyname > "interfejsu"\<interfacename1 > "i"\<defaultpropertyname > "interfejsu"\< interfacename2 > "
Interfejs dziedziczy dwa interfejsy, z których każdy deklaruje domyślna właściwość o tej samej nazwie. Kompilator nie można rozpoznać dostępu do tej właściwości domyślnej bez kwalifikacji. Ilustruje to poniższy przykład.  
  
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
  
 Po określeniu `testObj(1)`, kompilator próbuje rozpoznać ona domyślnej właściwości. Istnieją dwie właściwości domyślne możliwe z powodu dziedziczonych interfejsach, kompilator sygnały tego błędu.  
  
 **Identyfikator błędu:** BC30686  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Należy unikać dziedziczy wszystkie elementy członkowskie o takiej samej nazwie. W poprzednim przykładzie Jeśli `testObj` nie trzeba wykonać jedną z elementów członkowskich, na przykład, `Iface2`, Zadeklaruj go w następujący sposób:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     —lub—  
  
-   Implementuje dziedziczącej interfejsu w klasie. Następnie można wdrożyć wszystkich właściwości dziedziczonych pod różnymi nazwami. Jednak tylko jeden z nich może być domyślną właściwość klasy implementującej. Ilustruje to poniższy przykład.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
