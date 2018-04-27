---
title: Literał dokumentu XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c84fecbb035c229cc3576bc556db6ecb6f3934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-document-literal-visual-basic"></a>Literał dokumentu XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XDocument> obiektu.  
  
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
|`encoding`|Opcjonalna. Używa literały tekstowe zadeklarowanie, które kodowania dokumentu.|  
|`standalone`|Opcjonalna. Literały tekstowe. Musi być "tak" lub "no".|  
|`piCommentList`|Opcjonalna. Lista instrukcji przetwarzania XML i komentarze XML. Ma następujący format:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Każdy `piComment` może być jedną z następujących czynności:<br /><br /> -   [Literał instrukcji przetwarzającej kod XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Wymagana. Element główny dokumentu. Format jest jedną z następujących czynności:<br /><br /> <ul><li>[Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Osadzone wyrażenie w postaci `<%=` `elementExp` `%>`. `elementExp` Zwraca jedną z następujących czynności:<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> Obiektu.</li><li>Kolekcja, która zawiera jedną <xref:System.Xml.Linq.XElement> obiekt i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów.</li></ul></li></ul><br /> Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XDocument> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Literał dokumentu XML jest identyfikowany przez deklaracja XML na początku literału. Mimo że literał dokumentu XML musi mieć dokładnie jeden głównego elementu XML, może mieć dowolną liczbę instrukcji przetwarzania XML i komentarze XML.  
  
 Literał dokumentu XML nie może występować w elemencie XML.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza. Pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania <xref:System.Xml.Linq.XDocument.%23ctor%2A> i <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dokument XML zawierający deklaracja XML, instrukcji przetwarzania komentarz i element, który zawiera inny element.  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [Literał instrukcji przetwarzającej kod XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
