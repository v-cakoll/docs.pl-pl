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
ms.openlocfilehash: 927158f940d9b96cd06873c7d3e710be91b887e9
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071622"
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
|`object`|Wymagana. Kolekcja <xref:System.Xml.Linq.XElement> obiektów.|  
  
## <a name="return-value"></a>Wartość zwracana  
 A `String` zawierający wartość pierwszego elementu w kolekcji, lub `Nothing` Jeśli kolekcja jest pusta.  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Xml.Linq.XElement.Value%2A> Właściwości można łatwo uzyskać dostęp do wartości pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> obiektów. Ta właściwość najpierw sprawdza, czy kolekcja zawiera co najmniej jeden obiekt. Jeśli kolekcja jest pusta, ta właściwość zwraca `Nothing`. W przeciwnym razie ta właściwość zwraca wartość <xref:System.Xml.Linq.XElement.Value%2A> właściwości pierwszego elementu w kolekcji.  
  
> [!NOTE]
>  Jeśli dostęp do wartości atrybutu XML za pomocą "\@" identyfikator, wartość atrybutu jest zwracana jako `String` i nie trzeba jawnie określać <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.  
  
 Aby uzyskać dostęp do innych elementów w kolekcji, służy właściwość indeksatora rozszerzenia XML. Aby uzyskać więcej informacji, zobacz [właściwość indeksatora rozszerzenia](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Dziedziczenie  
 Większość użytkowników nie będzie konieczne wdrożenie <xref:System.Collections.Generic.IEnumerable%601>i w związku z tym można zignorować w tej sekcji.  
  
 <xref:System.Xml.Linq.XElement.Value%2A> Właściwość jest właściwością rozszerzenia dla typów implementujących `IEnumerable(Of XElement)`. Powiązanie tej właściwości rozszerzenia przypomina powiązania metody rozszerzenia: Jeśli typ implementuje jednego z interfejsów i definiuje właściwość o nazwie "Wartość", że właściwość ma pierwszeństwo przed właściwość rozszerzenia. Innymi słowy, to <xref:System.Xml.Linq.XElement.Value%2A> właściwość może zostać przesłonięta przez definiowanie nowych właściwości klasy, która implementuje `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie <xref:System.Xml.Linq.XElement.Value%2A> właściwości dostępu do pierwszego węzła w kolekcji <xref:System.Xml.Linq.XElement> obiektów. W przykładzie użyto właściwości osi elementu podrzędnego można pobrać kolekcji wszystkie węzły podrzędne o nazwie `phone` w `contact` obiektu.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać wartości atrybutu XML z kolekcją <xref:System.Xml.Linq.XAttribute> obiektów. W przykładzie użyto właściwości osi atrybutu, aby wyświetlić wartość `type` atrybutu dla wszystkich `phone` elementów.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Właściwość indeksatora rozszerzenia](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [Właściwości osi elementu podrzędnego XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Właściwości osi atrybutu XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
