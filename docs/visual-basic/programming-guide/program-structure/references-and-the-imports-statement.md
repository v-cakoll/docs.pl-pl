---
title: Referencje i importy — Instrukcja (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: bd08940ac04d0218f3d3936514a72c12449b34ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505565"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referencje i importy — Instrukcja (Visual Basic)
Można udostępnić zewnętrznych obiektów do projektu, wybierając **Dodaj odwołanie** polecenie **projektu** menu. Zestawy, które są podobne biblioteki typów, ale zawierają więcej informacji może wskazywać odwołania w języku Visual Basic.  
  
## <a name="the-imports-statement"></a>Importy — instrukcja  
 Zestawy zawierają jeden lub kilka przestrzeni nazw. Po dodaniu odwołania do zestawu, można również dodać `Imports` instrukcję, aby moduł, który kontroluje widoczność tego zestawu przestrzeni nazw, w module. `Imports` Instrukcja oferuje zakresu kontekstu, która umożliwia używanie tylko część obszaru nazw, trzeba podać unikatowy odwołanie.  
  
 `Imports` Instrukcji ma następującą składnię:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname` odnosi się do krótką nazwę, których można użyć w kodzie, do odwoływania się do importowanych przestrzeni nazw. `Namespace` jest dostępna za pośrednictwem jednej przestrzeni nazw odwołanie projektu za pomocą definicji w projekcie lub poprzedniej `Imports` instrukcji.  
  
 Moduł może zawierać dowolną liczbę `Imports` instrukcji. Muszą występować po każdym `Option` instrukcji, jeśli jest obecny, ale przed innymi kodami.  
  
> [!NOTE]
>  Nie należy mylić odwołania do projektu przy użyciu `Imports` instrukcji lub `Declare` instrukcji. Odwołania do projektu udostępnić zewnętrzne obiekty, takie jak obiekty w zestawach, do projektów Visual Basic. `Imports` Instrukcja jest używana, aby uprościć dostęp do odwołania do projektu, ale nie zapewnia dostępu do tych obiektów. `Declare` Instrukcja jest używana do zadeklarowania odwołania do zewnętrznej procedury biblioteki dołączanej (dynamicznie DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Aliasy użycia za pomocą Importy — instrukcja  
 `Imports` Instrukcji ułatwia dostęp do metod klas, eliminując konieczność jawnie wpisz w pełni kwalifikowane nazwy odwołań. Aliasy umożliwiają przypisywanie bardziej przyjaznej nazwy do tylko jednej części przestrzeni nazw. Na przykład sekwencji, który powoduje, że pojedynczy tekst do wyświetlenia w wielu wierszach CR/LF jest częścią <xref:Microsoft.VisualBasic.ControlChars> modułu w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. Aby użyć tej stałej w programie bez aliasu, należy wpisać następujący kod:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` instrukcje musi być zawsze pierwszych wierszy, natychmiast po dowolnej `Option` instrukcji w module. Poniższy fragment kodu przedstawia sposób importowania i przypisać aliasu do <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modułu:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Odwołania do tej przestrzeni nazw może być znacznie krótszy:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Jeśli `Imports` instrukcji nie ma nazwę aliasu, elementy zdefiniowane w importowanych przestrzeni nazw mogą być używane w module bez kwalifikacji. Jeśli określono nazwę aliasu, musi używać jako kwalifikator nazw zawartych w tej przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
