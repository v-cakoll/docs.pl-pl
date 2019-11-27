---
title: Literał dokumentu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: db77cccd26c87e271d6db45ce514ab6dabbc53e3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349384"
---
# <a name="xml-document-literal-visual-basic"></a>Literał dokumentu XML (Visual Basic)
Literał reprezentujący obiekt <xref:System.Xml.Linq.XDocument>.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`encoding`|Opcjonalna. Tekst literału deklarujący kodowanie używane przez dokument.|  
|`standalone`|Opcjonalna. Tekst literału. Musi mieć wartość "yes" lub "No".|  
|`piCommentList`|Opcjonalna. Lista instrukcji przetwarzania XML i komentarzy XML. Przyjmuje następujący format:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Każdy `piComment` może być jednym z następujących:<br /><br /> -   [literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Wymagana. Element główny dokumentu. Jest to jeden z następujących formatów:<br /><br /> <ul><li>[Literal elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Osadzone wyrażenie `<%=` formularza `elementExp` `%>`. `elementExp` zwraca jedną z następujących wartości:<br /><br /> <ul><li>Obiekt <xref:System.Xml.Linq.XElement>.</li><li>Kolekcja zawierająca jeden <xref:System.Xml.Linq.XElement> obiektu i dowolną liczbę obiektów <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment>.</li></ul></li></ul><br /> Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Uwagi  
 Literał dokumentu XML jest identyfikowany przez deklarację XML na początku literału. Chociaż każdy literał dokumentu XML musi mieć dokładnie jeden główny element XML, może zawierać dowolną liczbę instrukcji przetwarzania XML i komentarzy XML.  
  
 Literał dokumentu XML nie może występować w elemencie XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza. Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania konstruktorów <xref:System.Xml.Linq.XDocument.%23ctor%2A> i <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dokument XML, który ma deklarację XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Literał instrukcji przetwarzającej kod XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
