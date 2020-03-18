---
title: Użycie atrybutu (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668721"
---
# <a name="attributeusage-c"></a>Użycie atrybutu (C#)

Określa sposób użycia niestandardowej klasy atrybutów. <xref:System.AttributeUsageAttribute>jest atrybutem stosowanym do definicji atrybutów niestandardowych. Atrybut `AttributeUsage` umożliwia sterowanie:

- Do którego atrybutu elementów programu można zastosować. O ile nie ograniczysz jego użycia, atrybut może zostać zastosowany do jednego z następujących elementów programu:
  - zestaw
  - moduł
  - pole
  - event
  - method
  - Param
  - property
  - return
  - type
- Czy atrybut może być stosowany do jednego elementu programu wiele razy.
- Czy atrybuty są dziedziczone przez klasy pochodne.

Ustawienia domyślne wyglądają jak w poniższym przykładzie po zastosowaniu jawnie:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

W tym przykładzie `NewAttribute` klasy można zastosować do dowolnego obsługiwanego elementu programu. Ale może być stosowany tylko raz do każdej jednostki. Atrybut jest dziedziczony przez klasy pochodne po zastosowaniu do klasy podstawowej.

<xref:System.AttributeUsageAttribute.AllowMultiple> Argumenty <xref:System.AttributeUsageAttribute.Inherited> i są opcjonalne, więc następujący kod ma ten sam efekt:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

Pierwszy <xref:System.AttributeUsageAttribute> argument musi być jeden lub <xref:System.AttributeTargets> więcej elementów wyliczenia. Wiele typów docelowych można połączyć razem z operatorem OR, jak pokazano w poniższym przykładzie:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Począwszy od języka C# 7.3 atrybuty mogą być stosowane do właściwości lub pola zapasowego dla właściwości auto implemented. Atrybut ma zastosowanie do właściwości, chyba `field` że określono specyfikator w atrybucie. Oba przedstawiono w poniższym przykładzie:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument `true`jest , a następnie wynikowy atrybut można zastosować więcej niż jeden raz do jednej jednostki, jak pokazano w poniższym przykładzie:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

W takim `MultiUseAttribute` przypadku można stosować wielokrotnie, `AllowMultiple` ponieważ `true`jest ustawiona na . Oba formaty wyświetlane do stosowania wielu atrybutów są prawidłowe.

Jeśli <xref:System.AttributeUsageAttribute.Inherited> `false`jest , a następnie atrybut nie jest dziedziczony przez klasy pochodzące z klasy przypisanej. Przykład:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

W tym `NonInheritedAttribute` przypadku nie jest `DClass` stosowany do poprzez dziedziczenie.

## <a name="remarks"></a>Uwagi

Atrybut `AttributeUsage` jest atrybutem jednorazowego użytku — nie można go zastosować więcej niż jeden raz do tej samej klasy. `AttributeUsage`jest aliasem <xref:System.AttributeUsageAttribute>dla .

Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono <xref:System.AttributeUsageAttribute.Inherited> wpływ <xref:System.AttributeUsageAttribute.AllowMultiple> i <xref:System.AttributeUsageAttribute> argumenty do atrybutu i jak można wyliczyć atrybuty niestandardowe stosowane do klasy.

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

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Przewodnik programowania języka C#](../..//index.md)
- [Atrybuty](../../../..//standard/attributes/index.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty](index.md)
- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)
