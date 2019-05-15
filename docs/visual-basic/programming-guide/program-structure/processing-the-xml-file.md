---
title: Przetwarzanie pliku XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: ab05db770f312a362e26f17df684f6f4f49c0eb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586738"
---
# <a name="processing-the-xml-file-visual-basic"></a>Przetwarzanie pliku XML (Visual Basic)
Kompilator generuje ciąg Identyfikatora dla każdego konstrukcji w kodzie, który jest oznaczony do generowania dokumentacji. (Aby uzyskać informacje na temat tagów w kodzie, zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md).) Ciąg Identyfikatora jednoznacznie identyfikuje konstrukcja. Programów przetwarzających pliku XML można użyć ciąg Identyfikatora do identyfikowania odpowiadający element metadanych/odbicie .NET Framework.  
  
 Plik XML jest hierarchiczną reprezentację kodu; jest płaskiej listy przy użyciu wygenerowanego Identyfikatora dla każdego elementu.  
  
 Kompilator stosuje następujące reguły podczas generowania ciągi identyfikatorów:  
  
- Biały znak nie zostanie umieszczony w ciągu.  
  
- Pierwsza część ciąg Identyfikatora określa rodzaj elementu członkowskiego są identyfikowane za pomocą pojedynczy znak z dwukropkiem. Używane są następujące typy elementu członkowskiego.  
  
|Znak|Opis|  
|---|---|  
|N|— przestrzeń nazw<br /><br /> Nie można dodać komentarze dokumentacji do przestrzeni nazw, ale możesz wprowadzać CREF odwołania do nich, jeśli są obsługiwane.|  
|T|Typ: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|pole: `Dim`|  
|P|Właściwości: `Property` (w tym właściwości domyślne)|  
|M|Metoda: `Sub`, `Function`, `Declare`, `Operator`|  
|E|Zdarzenie: `Event`|  
|!|Ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o tym błędzie. Kompilator języka Visual Basic generuje informacje o błędzie dla łączy, których nie można rozpoznać.|  
  
- Druga część `String` jest w pełni kwalifikowana nazwa elementu, począwszy od głównego obszaru nazw. Nazwa elementu, jego typy otaczającej i przestrzeni nazw są oddzielone kropkami. Jeśli nazwa elementu zawiera kropek, są zastępowane przez znak numeru (#). Zakłada się, że żaden element ma znak liczby bezpośrednio w jego nazwę. Na przykład w pełni kwalifikowanej nazwy `String` będzie Konstruktor `System.String.#ctor`.  
  
- Dla właściwości i metod w przypadku argumentów dla metody, na liście argumentów w nawiasach jest zgodna. Jeśli nie ma żadnych argumentów, nawiasy nie są obecne. Argumenty są oddzielone przecinkami. Kodowanie każdego argumentu następuje bezpośrednio, jak jest zakodowany w podpisie .NET Framework.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie pokazano, jak identyfikator ciągi dla klasy i składowych są generowane.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Instrukcje: Tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
