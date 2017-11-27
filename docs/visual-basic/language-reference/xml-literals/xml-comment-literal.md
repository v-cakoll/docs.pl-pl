---
title: "Literał komentarza XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36be34ac22cfe926a2eea946f5e4c4eb534de696
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-literal-visual-basic"></a>Literał komentarza XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XComment> obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`<!--`|Wymagany. Oznacza początek komentarza XML.|  
|`content`|Wymagany. Tekst wyświetlany w komentarzu XML. Nie może zawierać szereg dwa łączniki (-) lub kończyć się łącznikiem sąsiadujące tagu zamykającego.|  
|`-->`|Wymagany. Oznacza koniec komentarza XML.|  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XComment> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Literały komentarza XML nie zawierają zawartości dokumentu; zawierają informacje o dokumentu. W sekcji komentarza XML kończy sekwencji "-->". Oznacza to następujące kwestie:  
  
-   Nie można użyć wyrażenia osadzonego w komentarzu XML literału, ponieważ ogranicznika wyrażenia osadzonego to prawidłowa zawartość komentarza XML.  
  
-   Sekcje komentarza XML nie mogą być zagnieżdżone, ponieważ `content` nie może zawierać wartości "-->".  
  
 Literał komentarza XML można przypisać do zmiennej lub można objąć literał elementu XML.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza. Ta funkcja umożliwia kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje literał komentarza XML na wywołanie <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy komentarz XML, który zawiera tekst "Jest komentarz".  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XComment>  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
