---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 84c3d175aede5d8066198592ffac601c0bd97620
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351831"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Określa, w jaki sposób można używać klasy atrybutów niestandardowych. `AttributeUsage` to atrybut, który można zastosować do definicji atrybutów niestandardowych w celu kontrolowania, jak można zastosować nowy atrybut. Ustawienia domyślne wyglądają następująco:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 W tym przykładzie Klasa `NewAttribute` może być stosowana do dowolnej jednostki kodu, która może być stosowana tylko raz do każdej jednostki. Jest dziedziczona przez klasy pochodne w przypadku zastosowania do klasy bazowej.  
  
 Argumenty `AllowMultiple` i `Inherited` są opcjonalne, więc ten kod ma ten sam skutek:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 Pierwszy argument `AttributeUsage` musi mieć co najmniej jeden element wyliczenia <xref:System.AttributeTargets>. Z operatorem OR można łączyć wiele typów docelowych, takich jak:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Jeśli argument `AllowMultiple` jest ustawiony na `true`, wówczas atrybut otrzymany można zastosować więcej niż raz do pojedynczej jednostki, na przykład:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 W tym przypadku `MultiUseAttr` można wielokrotnie zastosować, ponieważ `AllowMultiple` jest ustawiona na `true`. Oba formaty wyświetlane na potrzeby stosowania wielu atrybutów są prawidłowe.  
  
 Jeśli `Inherited` jest ustawiona na `false`, atrybut nie jest dziedziczony przez klasy, które pochodzą z klasy, która ma atrybut. Na przykład:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 W tym przypadku `Attr1` nie jest stosowany do `DClass` przez dziedziczenie.  
  
## <a name="remarks"></a>Uwagi  
 Atrybut `AttributeUsage` jest atrybutem pojedynczego użycia — nie można go zastosować więcej niż raz do tej samej klasy. `AttributeUsage` jest aliasem dla <xref:System.AttributeUsageAttribute>.  
  
 Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje wpływ argumentów `Inherited` i `AllowMultiple` na atrybut `AttributeUsage`, a także sposób wyliczania atrybutów niestandardowych zastosowanych do klasy.  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```console  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Przewodnik programowania Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
