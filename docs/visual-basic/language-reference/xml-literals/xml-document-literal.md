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
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400205"
---
# <a name="xml-document-literal-visual-basic"></a>Literał dokumentu XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XDocument> obiekt.  
  
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
|`encoding`|Opcjonalny. Tekst literału deklarujący kodowanie używane przez dokument.|  
|`standalone`|Opcjonalny. Tekst literału. Musi mieć wartość "yes" lub "No".|  
|`piCommentList`|Opcjonalny. Lista instrukcji przetwarzania XML i komentarzy XML. Przyjmuje następujący format:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Każdy `piComment` z nich może być jednym z następujących:<br /><br /> -   [Literał instrukcji przetwarzania XML](xml-processing-instruction-literal.md).<br />-   [Literał komentarza XML](xml-comment-literal.md).|  
|`rootElement`|Wymagany. Element główny dokumentu. Jest to jeden z następujących formatów:<br /><br /> <ul><li>[Literal elementu XML](xml-element-literal.md).</li><li>Wyrażenie osadzone formularza `<%=` `elementExp` `%>` . `elementExp`Zwraca jedną z następujących wartości:<br /><br /> <ul><li>Obiekt <xref:System.Xml.Linq.XElement>.</li><li>Kolekcja zawierająca jeden <xref:System.Xml.Linq.XElement> obiekt i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment> obiektów i.</li></ul></li></ul><br /> Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Uwagi  
 Literał dokumentu XML jest identyfikowany przez deklarację XML na początku literału. Chociaż każdy literał dokumentu XML musi mieć dokładnie jeden główny element XML, może zawierać dowolną liczbę instrukcji przetwarzania XML i komentarzy XML.  
  
 Literał dokumentu XML nie może występować w elemencie XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza. Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania <xref:System.Xml.Linq.XDocument.%23ctor%2A> <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorów i.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dokument XML, który ma deklarację XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Literał instrukcji przetwarzającej kod XML](xml-processing-instruction-literal.md)
- [Literał komentarza XML](xml-comment-literal.md)
- [Literał elementu XML](xml-element-literal.md)
- [Literały XML](index.md)
- [Tworzenie XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
