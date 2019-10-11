---
title: Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego elementu członkowskiego interfejsu "<defaultpropertyname>" interfejsu "<interfacename1>" i "<defaultpropertyname>" interfejsu "<interfacename2>"
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: f76163d58f3f11d3ca946525a1604abc3ebba68d
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250366"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>Dostęp do właściwości domyślnej jest niejednoznaczny dla dziedziczonego elementu członkowskiego interfejsu "\<defaultpropertyname >" interfejsu "\<interfacename1 >" i "\<defaultpropertyname >" interfejsu "\<interfacename2 >"

Interfejs dziedziczy z dwóch interfejsów, z których każdy deklaruje właściwość domyślną o tej samej nazwie. Kompilator nie może rozpoznać dostępu do tej właściwości domyślnej bez kwalifikacji. Ilustruje to Poniższy przykład.

```vb
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

Po określeniu `testObj(1)` kompilator próbuje rozwiązać ten problem do właściwości domyślnej. Istnieją jednak dwie możliwe właściwości domyślne ze względu na dziedziczone interfejsy, więc kompilator sygnalizuje ten błąd.

**Identyfikator błędu:** BC30686

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Należy unikać dziedziczenia wszystkich elementów członkowskich o tej samej nazwie. W poprzednim przykładzie, jeśli `testObj` nie potrzebuje żadnego z elementów członkowskich, powiedz `Iface2`, a następnie zadeklaruj go w następujący sposób:

  ```vb
  Dim testObj As Iface1
  ```

  \-or-

- Zaimplementuj interfejs dziedziczenia w klasie. Następnie można zaimplementować każdą z dziedziczonych właściwości o różnych nazwach. Jednak tylko jeden z nich może być właściwością domyślną klasy implementującej. Ilustruje to Poniższy przykład.

  ```vb
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

- [Interfejsów](../../programming-guide/language-features/interfaces/index.md)
