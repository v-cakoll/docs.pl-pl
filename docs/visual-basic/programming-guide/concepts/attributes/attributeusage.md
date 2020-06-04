---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400735"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)

Określa, w jaki sposób można używać klasy atrybutów niestandardowych. `AttributeUsage`jest atrybutem, który można zastosować do definicji atrybutów niestandardowych w celu kontrolowania, jak można zastosować nowy atrybut. Ustawienia domyślne wyglądają następująco:

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

W tym przykładzie `NewAttribute` Klasa może być stosowana do dowolnej jednostki kodu, która może być stosowana tylko raz do każdej jednostki. Jest dziedziczona przez klasy pochodne w przypadku zastosowania do klasy bazowej.

`AllowMultiple`Argumenty i `Inherited` są opcjonalne, więc ten kod ma ten sam skutek:

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

Pierwszy `AttributeUsage` argument musi być co najmniej jednym elementem <xref:System.AttributeTargets> wyliczenia. Z operatorem OR można łączyć wiele typów docelowych, takich jak:

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

Jeśli `AllowMultiple` argument jest ustawiony na `true` , wówczas atrybut otrzymany można zastosować więcej niż raz do pojedynczej jednostki, tak jak to:

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

W takim przypadku `MultiUseAttr` można je zastosować wielokrotnie `AllowMultiple` , ponieważ jest ustawiona na `true` . Oba formaty wyświetlane na potrzeby stosowania wielu atrybutów są prawidłowe.

Jeśli `Inherited` jest ustawiona na `false` , atrybut nie jest dziedziczony przez klasy, które pochodzą z klasy, która ma atrybut. Przykład:

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

W tym przypadku `Attr1` nie ma zastosowania do `DClass` dziedziczenia.

## <a name="remarks"></a>Uwagi

`AttributeUsage`Atrybut jest atrybutem o pojedynczym użyciu — nie można go zastosować więcej niż raz do tej samej klasy. `AttributeUsage`jest aliasem dla <xref:System.AttributeUsageAttribute> .

Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje efekt `Inherited` `AllowMultiple` argumentów i do `AttributeUsage` atrybutu oraz sposób wyliczania atrybutów niestandardowych zastosowanych do klasy.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Przewodnik programowania w Visual Basic](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../reflection.md)
- [Atrybuty (Visual Basic)](../../../language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](accessing-attributes-by-using-reflection.md)
