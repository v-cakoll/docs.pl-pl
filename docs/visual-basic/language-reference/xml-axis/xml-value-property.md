---
title: Właściwość wartości XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592005"
---
# <a name="xml-value-property-visual-basic"></a>Właściwość wartości XML (Visual Basic)

Zapewnia dostęp do wartości pierwszego elementu kolekcji obiektów <xref:System.Xml.Linq.XElement>.

## <a name="syntax"></a>Składnia

```vb
object.Value
```

## <a name="parts"></a>Części

|Termin|Definicja|  
|---|---|  
|`object`|Wymagany. Kolekcja obiektów <xref:System.Xml.Linq.XElement>.|  

## <a name="return-value"></a>Wartość zwracana

 @No__t-0 zawiera wartość pierwszego elementu kolekcji lub `Nothing`, jeśli kolekcja jest pusta.

## <a name="remarks"></a>Uwagi

 Właściwość <xref:System.Xml.Linq.XElement.Value%2A> ułatwia dostęp do wartości pierwszego elementu w kolekcji obiektów <xref:System.Xml.Linq.XElement>. Ta właściwość najpierw sprawdza, czy kolekcja zawiera co najmniej jeden obiekt. Jeśli kolekcja jest pusta, ta właściwość zwraca `Nothing`. W przeciwnym razie ta właściwość zwraca wartość właściwości <xref:System.Xml.Linq.XElement.Value%2A> pierwszego elementu w kolekcji.

> [!NOTE]
> Gdy uzyskujesz dostęp do wartości atrybutu XML przy użyciu identyfikatora "\@", wartość atrybutu jest zwracana jako `String` i nie musisz jawnie określać właściwości <xref:System.Xml.Linq.XAttribute.Value%2A>.

 Aby uzyskać dostęp do innych elementów w kolekcji, można użyć właściwości indeksatora rozszerzenia XML. Aby uzyskać więcej informacji, zobacz [Extension Indexer właściwości](extension-indexer-property.md).

## <a name="inheritance"></a>Dziedziczenie

 Większość użytkowników nie będzie musiała implementować <xref:System.Collections.Generic.IEnumerable%601> i w związku z tym można zignorować tę sekcję.

 Właściwość <xref:System.Xml.Linq.XElement.Value%2A> jest właściwością rozszerzenia dla typów, które implementują `IEnumerable(Of XElement)`. Powiązanie tej właściwości rozszerzenia jest podobne do powiązania metod rozszerzających: Jeśli typ implementuje jeden z interfejsów i definiuje właściwość o nazwie "value", ta właściwość ma pierwszeństwo przed właściwością rozszerzenia. Innymi słowy, ta właściwość <xref:System.Xml.Linq.XElement.Value%2A> może zostać przesłonięta przez zdefiniowanie nowej właściwości w klasie implementującej `IEnumerable(Of XElement)`.

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać właściwości <xref:System.Xml.Linq.XElement.Value%2A> w celu uzyskania dostępu do pierwszego węzła w kolekcji obiektów <xref:System.Xml.Linq.XElement>. W przykładzie użyta jest właściwość oś podrzędna do pobrania kolekcji wszystkich węzłów podrzędnych o nazwie `phone`, które znajdują się w obiekcie `contact`.

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 Ten kod wyświetla następujący tekst:

 `Phone number: 206-555-0144`

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak pobrać wartość atrybutu XML z kolekcji obiektów <xref:System.Xml.Linq.XAttribute>. W przykładzie użyta jest właściwość osi atrybutu w celu wyświetlenia wartości atrybutu `type` dla wszystkich elementów `phone`.

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 Ten kod wyświetla następujący tekst:

 ```console
 home
 work
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Właściwości osi XML](index.md)
- [Literały XML](../xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Metody rozszerzeń](../../programming-guide/language-features/procedures/extension-methods.md)
- [Właściwość indeksatora rozszerzenia](extension-indexer-property.md)
- [Właściwości osi elementu podrzędnego XML](xml-child-axis-property.md)
- [Właściwości osi atrybutu XML](xml-attribute-axis-property.md)
