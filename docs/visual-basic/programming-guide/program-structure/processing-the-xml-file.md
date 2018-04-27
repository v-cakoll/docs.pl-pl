---
title: Przetwarzanie pliku XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 86dae99f2d17a506a27cf491a76083df618ba27b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="processing-the-xml-file-visual-basic"></a>Przetwarzanie pliku XML (Visual Basic)
Kompilator generuje ciąg Identyfikatora dla każdego konstrukcji w kodzie zostanie oznaczony do generowania dokumentacji. (Aby uzyskać informacje na temat tagów w kodzie, zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) Ciąg Identyfikatora unikatowo identyfikuje konstrukcja. Programy, które przetwarzają plik XML umożliwiają identyfikowanie odpowiedni ciąg Identyfikatora [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] elementu metadanych/odbicia.  
  
 Plik XML nie jest hierarchiczną reprezentację kodu; jest płaska lista z Identyfikatorem wygenerowany dla każdego elementu.  
  
 Kompilator stosuje następujące reguły podczas generowania ciągi identyfikatorów:  
  
-   Nie biały znak jest umieszczona w ciągu.  
  
-   Pierwsza część ciąg Identyfikatora określa rodzaj elementu członkowskiego jest określony, z jednego znaku z dwukropkiem. Używane są następujące typy elementu członkowskiego.  
  
|Znak|Opis|  
|---|---|  
|N|— przestrzeń nazw<br /><br /> Nie można dodać komentarze dokumentacji do przestrzeni nazw, ale możesz wprowadzić CREF odwołania do nich, jeśli są obsługiwane.|  
|T|Typ: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|pola: `Dim`|  
|P|Właściwości: `Property` (w tym właściwości domyślne)|  
|M|Metoda: `Sub`, `Function`, `Declare`, `Operator`|  
|E|Zdarzenie: `Event`|  
|!|Ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o tym błędzie. Kompilator Visual Basic generuje informacje o błędzie dla łącza, które nie zostały rozpoznane.|  
  
-   Druga część `String` jest w pełni kwalifikowana nazwa elementu, zaczynając od katalogu głównego przestrzeni nazw. Nazwa elementu, jego typ otaczający i przestrzeni nazw są oddzielone kropkami. Jeśli nazwa elementu zawiera okresów, są one zastąpione znakiem numeru (#). Zakłada się, że żadne pozycje nie znak liczby bezpośrednio w swoim imieniu. Na przykład w pełni kwalifikowana nazwa `String` byłoby konstruktora `System.String.#ctor`.  
  
-   Dla właściwości i metody w przypadku argumentów dla metody, ujęte w nawiasy listy argumentów jest zgodna. Jeśli nie ma żadnych argumentów, nawiasów, nie są dostępne. Argumenty są oddzielone przecinkami. Kodowanie każdy argument następuje bezpośrednio jak jest zakodowany w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] podpisu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób identyfikator ciągi dla klasy i jej elementów członkowskich są generowane.  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
