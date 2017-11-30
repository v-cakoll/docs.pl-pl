---
title: "Właściwość indeksatora rozszerzenia (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a>Właściwość indeksatora rozszerzenia (Visual Basic)
Zapewnia dostęp do poszczególnych elementów w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
object(index)  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`object`|Wymagany. Kolekcja z obsługą zapytań. Oznacza to, że kolekcja, która implementuje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.|  
|(|Wymagany. Oznacza początek właściwości indeksatora.|  
|`index`|Wymagany. Wyrażenie liczba całkowita określająca liczona od zera pozycja elementu kolekcji.|  
|)|Wymagany. Oznacza koniec właściwości indeksatora.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt z określonej lokalizacji w kolekcji lub `Nothing` Jeśli indeks jest poza zakresem.  
  
## <a name="remarks"></a>Uwagi  
 Właściwość indeksatora rozszerzenia służy do dostęp do poszczególnych elementów w kolekcji. Ta właściwość indeksatora jest zwykle używana w danych wyjściowych właściwości osi XML. Elementu podrzędnego XML i właściwości osi descendant XML zwracają kolekcje <xref:System.Xml.Linq.XElement> obiektów lub wartość atrybutu.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje właściwości indeksatora rozszerzenia wywołań `ElementAtOrDefault` metody. W przeciwieństwie do indeksatora tablicy `ElementAtOrDefault` metoda zwraca `Nothing` Jeśli indeks jest poza zakresem. To zachowanie jest przydatne, gdy nie można określić, że liczba elementów w kolekcji.  
  
 Ta właściwość indeksatora przypomina właściwość rozszerzenia dla kolekcji, które implementują <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>: jest używany tylko wtedy, gdy kolekcja nie ma indeksatora lub domyślnej właściwości.  
  
 Aby uzyskać dostęp do wartości pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty, można użyć pliku XML `Value` właściwości. Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie indeksatora rozszerzenia dostępu do drugiego węzła podrzędnego w kolekcji <xref:System.Xml.Linq.XElement> obiektów. Kolekcja jest dostępny za pomocą właściwości osi podrzędnej, która pobiera wszystkie elementy podrzędne o nazwie `phone` w `contact` obiektu.  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
