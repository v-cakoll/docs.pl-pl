---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Określa sposób użycia klasy atrybutu niestandardowego. <xref:System.AttributeUsageAttribute> jest stosowany do definicji atrybutu niestandardowego atrybutu. `AttributeUsage` Atrybutu umożliwia kontrolowanie:

- Atrybut, którego elementy program może być stosowany do. Jeśli nie ograniczysz jest użycie atrybutu może być stosowany do żadnego z następujących elementów programu:
  - zestaw
  - moduł
  - pole
  - zdarzenie
  - — metoda
  - Param
  - property
  - return
  - — typ
- Określa, czy atrybut można stosować do jednego elementu programu wiele razy.
- Określa, czy atrybuty są dziedziczone przez klasy pochodnej.

Ustawienia domyślne wyglądać jak w następującym przykładzie jawnie stosowania:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

W tym przykładzie `NewAttribute` klasy mogą być stosowane do dowolnego elementu obsługiwanych programu. Ale można go zastosować tylko raz do każdej jednostki. Ten atrybut jest dziedziczona przez klas pochodnych po zastosowaniu do klasy podstawowej.

<xref:System.AttributeUsageAttribute.AllowMultiple> i <xref:System.AttributeUsageAttribute.Inherited> argumenty są opcjonalne, dzięki czemu następujący kod mają ten sam efekt:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

Pierwszy <xref:System.AttributeUsageAttribute> argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia. Wiele typów docelowy może odnosić się wraz z operatora OR, podobnie jak w poniższym przykładzie przedstawiono:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Począwszy od 7.3 C#, atrybuty można zastosować do właściwość lub pole zapasowe dla automatycznie implementowanej właściwości. Ten atrybut ma zastosowanie do właściwości, chyba że zostanie `field` Specyfikator atrybutu. W poniższym przykładzie przedstawiono zarówno:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument jest `true`, a następnie wynikowy atrybut można stosować więcej niż raz do jednej jednostki, jak pokazano w poniższym przykładzie:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

W takim przypadku `MultiUseAttribute` może odnosić się wielokrotnie ponieważ `AllowMultiple` ma ustawioną wartość `true`. Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.

Jeśli <xref:System.AttributeUsageAttribute.Inherited> jest `false`, a następnie ten atrybut nie jest dziedziczone przez klasy pochodnej z klasy oparte na atrybutach. Na przykład:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

W takim przypadku `NonInheritedAttribute` nie jest stosowana do `DClass` za pośrednictwem dziedziczenia.

## <a name="remarks"></a>Uwagi

`AttributeUsage` Jest atrybutem jednorazowy — nie można zastosować w więcej niż raz do tej samej klasy. `AttributeUsage` alias jest <xref:System.AttributeUsageAttribute>.

Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje efekt <xref:System.AttributeUsageAttribute.Inherited> i <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty <xref:System.AttributeUsageAttribute> atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a>Zobacz też
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Przewodnik programowania w języku C#](../..//index.md)  
 [Atrybuty](../../../..//standard/attributes/index.md)  
 [Odbicie (C#)](../reflection.md)  
 [Atrybuty](index.md)  
 [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)
