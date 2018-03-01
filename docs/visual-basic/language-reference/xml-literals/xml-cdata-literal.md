---
title: "Literał CDATA XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 906fd2494dd952c08088b9b7e38dba4505780481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-cdata-literal-visual-basic"></a>Literał CDATA XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XCData> obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Części  
 `<![CDATA[`  
 Wymagany. Oznacza początek sekcji XML CDATA.  
  
 `content`  
 Wymagany. Zawartość tekstowa pojawią się w sekcji XML CDATA.  
  
 `]]>`  
 Wymagany. Oznacza koniec sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XCData> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Sekcji XML CDATA zawiera pierwotne tekst, który powinny być włączone, lecz nie przeanalizować, XML, który go zawiera. Sekcja XML CDATA mogą zawierać dowolny tekst. W tym zarezerwowanych znaków XML. W sekcji XML CDATA kończy sekwencja "]] >". Oznacza to następujące kwestie:  
  
-   Nie można użyć wyrażenia osadzonego w literał CDATA XML, ponieważ prawidłowa zawartość XML CDATA są ograniczniki wyrażenia osadzonego.  
  
-   Nie można zagnieździć sekcji XML CDATA, ponieważ `content` nie może zawierać wartości "]] >".  
  
 Można przypisać literał CDATA XML do zmiennej lub objąć literał elementu XML.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy, ale nie są używane znaki kontynuacji wiersza. Dzięki temu można kopiować zawartości z dokumentu XML i wklej go bezpośrednio do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje literał CDATA XML do wywołania <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sekcji CDATA, która zawiera tekst "może zawierać literału \<XML > tagi".  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XCData>  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
