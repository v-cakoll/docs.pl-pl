---
title: AttributeUsage (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f358068d00c042a979216cdda51dcc7e07abbc5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Określa sposób użycia klasy atrybutu niestandardowego. `AttributeUsage`jest atrybut, który może odnosić się do definicji atrybutu niestandardowego do kontrolowania, jak można zastosować nowego atrybutu. Po zastosowaniu jawnie, domyślne ustawienia następującą postać:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 W tym przykładzie `NewAttribute` klasa może być stosowane do dowolnej jednostki kodu atrybutu można, ale mogą być stosowane tylko raz do każdej jednostki. Zostało ono odziedziczone przez klas pochodnych po zastosowaniu do klasy podstawowej.  
  
 `AllowMultiple` i `Inherited` argumenty są opcjonalne, dlatego ten kod działa tak samo:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 Pierwszy `AttributeUsage` argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia. Wiele typów docelowy może odnosić się wraz z operatora OR w następujący sposób:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Jeśli `AllowMultiple` argument ma wartość `true`, następnie wynikowy atrybut można stosować więcej niż raz do jednej jednostki, takich jak to:  
  
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
  
 W takim przypadku `MultiUseAttr` może odnosić się wielokrotnie ponieważ `AllowMultiple` ma ustawioną wartość `true`. Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.  
  
 Jeśli `Inherited` ma ustawioną wartość `false`, a następnie ten atrybut nie jest dziedziczone przez klasy, które są pochodnymi klasy, która ma atrybut. Na przykład:  
  
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
  
 W takim przypadku `Attr1` nie ma zastosowania do `DClass` za pośrednictwem dziedziczenia.  
  
## <a name="remarks"></a>Uwagi  
 `AttributeUsage` Jest atrybutem jednorazowy — nie można zastosować w więcej niż raz do tej samej klasy. `AttributeUsage`alias jest <xref:System.AttributeUsageAttribute>.  
  
 Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje efekt `Inherited` i `AllowMultiple` argumenty `AttributeUsage` atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.  
  
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
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Atrybuty](../../../../standard/attributes/index.md)  
 [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
