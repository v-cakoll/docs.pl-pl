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
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942978"
---
# <a name="xml-value-property-visual-basic"></a>Właściwość wartości XML (Visual Basic)
Zapewnia dostęp do wartości pierwszego elementu kolekcji <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`object`|Wymagane. <xref:System.Xml.Linq.XElement> Kolekcja obiektów.|  
  
## <a name="return-value"></a>Wartość zwracana  
 A `String` , który zawiera wartość pierwszego elementu kolekcji lub `Nothing` Jeśli kolekcja jest pusta.  
  
## <a name="remarks"></a>Uwagi  
 Właściwość ułatwia dostęp do wartości pierwszego elementu w <xref:System.Xml.Linq.XElement> kolekcji obiektów. <xref:System.Xml.Linq.XElement.Value%2A> Ta właściwość najpierw sprawdza, czy kolekcja zawiera co najmniej jeden obiekt. Jeśli kolekcja jest pusta, ta właściwość zwraca `Nothing`. W przeciwnym razie ta właściwość zwraca wartość <xref:System.Xml.Linq.XElement.Value%2A> właściwości pierwszego elementu w kolekcji.  
  
> [!NOTE]
> Gdy uzyskujesz dostęp do wartości atrybutu XML przy użyciu identyfikatora "\@", wartość atrybutu jest zwracana `String` jako i nie <xref:System.Xml.Linq.XAttribute.Value%2A> trzeba jawnie określać właściwości.  
  
 Aby uzyskać dostęp do innych elementów w kolekcji, można użyć właściwości indeksatora rozszerzenia XML. Aby uzyskać więcej informacji, zobacz [Extension Indexer właściwości](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Dziedziczenie  
 Większość użytkowników nie musi implementować <xref:System.Collections.Generic.IEnumerable%601>i w związku z tym będzie można zignorować tę sekcję.  
  
 Właściwość jest właściwością rozszerzenia dla typów, które implementują `IEnumerable(Of XElement)`. <xref:System.Xml.Linq.XElement.Value%2A> Powiązanie tej właściwości rozszerzenia jest podobne do powiązania metod rozszerzających: Jeśli typ implementuje jeden z interfejsów i definiuje właściwość o nazwie "value", ta właściwość ma pierwszeństwo przed właściwością rozszerzenia. Innymi słowy, ta <xref:System.Xml.Linq.XElement.Value%2A> właściwość może zostać przesłonięta przez zdefiniowanie nowej właściwości w klasie implementującej. `IEnumerable(Of XElement)`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, <xref:System.Xml.Linq.XElement.Value%2A> jak używać właściwości, aby uzyskać dostęp do pierwszego węzła w <xref:System.Xml.Linq.XElement> kolekcji obiektów. W przykładzie użyta jest właściwość oś podrzędna do pobrania kolekcji wszystkich węzłów podrzędnych o `phone` nazwie, które znajdują się `contact` w obiekcie.  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać wartość atrybutu XML z kolekcji <xref:System.Xml.Linq.XAttribute> obiektów. W przykładzie użyta jest właściwość osi atrybutu w celu wyświetlenia wartości `type` atrybutu dla wszystkich `phone` elementów.  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Właściwość indeksatora rozszerzenia](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [Właściwości osi elementu podrzędnego XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Właściwości osi atrybutu XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
