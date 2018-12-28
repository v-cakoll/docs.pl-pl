---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 081a8f6edcddd5e87d3d9750b91ff42a72b92886
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656352"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Określa, jak używać klasy atrybutu niestandardowego. <xref:System.AttributeUsageAttribute> jest atrybutem stosowanych do definicji atrybutu niestandardowego. `AttributeUsage` Atrybut umożliwia kontrolowanie:

- Atrybut elementy programu, którego można stosować do. Chyba, że możesz ograniczyć jego użycia, atrybut można stosować do dowolnej z następujących elementów programu:
  - zestaw
  - moduł
  - pole
  - zdarzenie
  - — metoda
  - param
  - property
  - return
  - — typ
- Czy atrybut można stosować do jednego elementu programu wiele razy.
- Czy atrybuty są dziedziczone przez klasy pochodne.

Ustawienia domyślne wyglądać jak w poniższym przykładzie, po zastosowaniu jawnie:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

W tym przykładzie `NewAttribute` klasy mogą być stosowane do dowolnego elementu obsługiwany program. Ale można go zastosować tylko raz do każdej jednostki. Ten atrybut jest dziedziczone przez klasy pochodne, gdy jest stosowany do klasy bazowej.

<xref:System.AttributeUsageAttribute.AllowMultiple> i <xref:System.AttributeUsageAttribute.Inherited> argumenty są opcjonalne, więc poniższy kod działa tak samo:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

Pierwszy <xref:System.AttributeUsageAttribute> argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia. Wiele typów docelowych, mogą być połączone wraz z operatorem OR, podobnie jak w poniższym przykładzie pokazano:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Począwszy od języka C# 7.3 można można zastosować atrybutów do właściwość lub pole zapasowe dla automatycznie implementowanej właściwości. Ten atrybut ma zastosowanie do właściwości, chyba że określisz `field` specyfikator w atrybucie. Oba są wyświetlane w następującym przykładzie:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument jest `true`, a następnie wynikowy atrybut można stosować więcej niż jeden raz do jednej jednostki, jak pokazano w poniższym przykładzie:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

W tym przypadku `MultiUseAttribute` mogą być stosowane wielokrotnie, ponieważ `AllowMultiple` ustawiono `true`. Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.

Jeśli <xref:System.AttributeUsageAttribute.Inherited> jest `false`, a następnie ten atrybut nie jest dziedziczone przez klasy pochodne od klas opartego na atrybutach. Na przykład:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

W tym przypadku `NonInheritedAttribute` nie jest stosowane do `DClass` za pomocą dziedziczenia.

## <a name="remarks"></a>Uwagi

`AttributeUsage` Atrybut jest atrybutem jednorazowy — nie można zastosować w więcej niż jeden raz do tej samej klasy. `AttributeUsage` jest aliasem <xref:System.AttributeUsageAttribute>.

Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

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

- <xref:System.Attribute>  
- <xref:System.Reflection>  
- [Przewodnik programowania w języku C#](../..//index.md)  
- [Atrybuty](../../../..//standard/attributes/index.md)  
- [Odbicie (C#)](../reflection.md)  
- [Atrybuty](index.md)  
- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)
