---
title: Literał instrukcji przetwarzającej kod XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347043"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literał instrukcji przetwarzającej kod XML (Visual Basic)
Literał reprezentujący obiekt <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Części  
 `<?`  
 Wymagana. Wskazuje początek literału instrukcji przetwarzania XML.  
  
 `piName`  
 Wymagana. Nazwa wskazująca, która aplikacja jest celem instrukcji przetwarzania. Nie można rozpocząć od "XML" lub "XML".  
  
 `piData`  
 Opcjonalna. Ciąg wskazujący, w jaki sposób aplikacja, do której należy `piName`, powinna przetwarzać dokument XML.  
  
 `?>`  
 Wymagana. Oznacza koniec instrukcji przetwarzania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Uwagi  
 Literały instrukcji przetwarzania XML wskazują, w jaki sposób aplikacje powinny przetwarzać dokument XML. Gdy aplikacja ładuje dokument XML, aplikacja może sprawdzić instrukcje przetwarzania XML, aby określić sposób przetwarzania dokumentu. Aplikacja interpretuje znaczenie `piName` i `piData`.  
  
 Literał dokumentu XML używa składni podobnej do tej instrukcji przetwarzania XML. Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> Element `piName` nie może rozpoczynać się od ciągu "XML" lub "XML", ponieważ specyfikacja XML 1,0 rezerwuje te identyfikatory.  
  
 Do zmiennej można przypisać literał instrukcji przetwarzania XML lub dodać go do literału dokumentu XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy bez znaków kontynuacji wiersza. Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał instrukcji przetwarzania XML na wywołanie konstruktora <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy instrukcję przetwarzania identyfikującą arkusz stylów dla dokumentu XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
