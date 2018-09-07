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
ms.openlocfilehash: 2b0719320db5843d5d010bfbd70e551646e3ded9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086342"
---
# <a name="xml-value-property-visual-basic"></a>Właściwość wartości XML (Visual Basic)
Zapewnia dostęp do wartości pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`object`|Wymagane. Kolekcja <xref:System.Xml.Linq.XElement> obiektów.|  
  
## <a name="return-value"></a>Wartość zwracana  
 A `String` zawierający wartość pierwszego elementu w kolekcji, lub `Nothing` Jeśli kolekcja jest pusta.  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Xml.Linq.XElement.Value%2A> Właściwość ułatwia dostęp do wartości pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów. Właściwość ta najpierw sprawdza, czy kolekcja zawiera co najmniej jeden obiekt. Jeśli kolekcja jest pusta, właściwość ta zwraca `Nothing`. W przeciwnym razie ta właściwość zwraca wartość <xref:System.Xml.Linq.XElement.Value%2A> właściwości pierwszego elementu w kolekcji.  
  
> [!NOTE]
>  Jeśli uzyskujesz dostęp do wartości atrybutu XML przy użyciu "\@" identyfikator, wartość atrybutu jest zwracana jako `String` i nie trzeba jawnie określić <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.  
  
 Aby uzyskać dostęp do innych elementów w kolekcji, służy właściwość indeksatora rozszerzenia XML. Aby uzyskać więcej informacji, zobacz [właściwość indeksatora rozszerzenia](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Dziedziczenie  
 Większość użytkowników nie trzeba implementować <xref:System.Collections.Generic.IEnumerable%601>i dlatego można zignorować tę sekcję.  
  
 <xref:System.Xml.Linq.XElement.Value%2A> Właściwość jest właściwością rozszerzenia dla typów, które implementują `IEnumerable(Of XElement)`. Powiązanie tej właściwości rozszerzenia przypomina powiązanie metody rozszerzenia: Jeśli typ implementuje jednego z interfejsów i definiuje właściwość o nazwie "Value", ta właściwość ma pierwszeństwo przed właściwość rozszerzenia. Innymi słowy, to <xref:System.Xml.Linq.XElement.Value%2A> właściwość może być zastąpiona przez zdefiniowanie nowej właściwości w klasie, która implementuje `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać <xref:System.Xml.Linq.XElement.Value%2A> właściwości dostępu do pierwszego węzła w zbiorze <xref:System.Xml.Linq.XElement> obiektów. W przykładzie użyto właściwości osi elementu podrzędnego można pobrać kolekcji wszystkie węzły podrzędne, o nazwie `phone` znajdujących się w `contact` obiektu.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można uzyskać wartości atrybutu XML z kolekcją <xref:System.Xml.Linq.XAttribute> obiektów. W przykładzie użyto właściwości osi atrybutu, aby wyświetlić wartość `type` atrybutu dla wszystkich `phone` elementów.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Właściwość indeksatora rozszerzenia](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [Właściwości osi elementu podrzędnego XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Właściwości osi atrybutu XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
