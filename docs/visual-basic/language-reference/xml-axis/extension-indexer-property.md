---
title: Właściwość indeksatora rozszerzenia (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582183"
---
# <a name="extension-indexer-property-visual-basic"></a>Właściwość indeksatora rozszerzenia (Visual Basic)
Zapewnia dostęp do poszczególnych elementów w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`object`|Wymagany. Kolekcja queryable. Oznacza to, że kolekcja implementująca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.|  
|(|Wymagany. Wskazuje początek właściwości indeksatora.|  
|`index`|Wymagany. Wyrażenie liczb całkowitych określające pozycję elementu w kolekcji liczony od zera.|  
|)|Wymagany. Oznacza koniec właściwości indeksatora.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt z określonej lokalizacji w kolekcji lub `Nothing`, jeśli indeks jest poza zakresem.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać dostęp do poszczególnych elementów w kolekcji, można użyć właściwości indeksatora rozszerzenia. Ta właściwość indeksatora jest zwykle używana w danych wyjściowych właściwości osi XML. Właściwości osi elementów potomnych XML i XML zwracają kolekcje <xref:System.Xml.Linq.XElement> obiektów lub wartości atrybutu.  
  
 Kompilator Visual Basic konwertuje właściwości indeksatora rozszerzenia na wywołania metody `ElementAtOrDefault`. W przeciwieństwie do indeksatora tablicy Metoda `ElementAtOrDefault` zwraca `Nothing`, jeśli indeks jest poza zakresem. To zachowanie jest przydatne, gdy nie można łatwo określić liczby elementów w kolekcji.  
  
 Ta właściwość indeksatora jest taka sama jak Właściwość rozszerzenia dla kolekcji implementujących <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>: jest używana tylko wtedy, gdy kolekcja nie ma indeksatora ani właściwości domyślnej.  
  
 Aby uzyskać dostęp do wartości pierwszego elementu w kolekcji obiektów <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, można użyć właściwości XML `Value`. Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak za pomocą indeksatora rozszerzeń uzyskać dostęp do drugiego węzła podrzędnego w kolekcji obiektów <xref:System.Xml.Linq.XElement>. Do kolekcji uzyskuje się dostęp za pomocą Właściwości oś podrzędna, która pobiera wszystkie elementy podrzędne o nazwie `phone` w obiekcie `contact`.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
