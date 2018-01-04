---
title: "Referencje i importy — Instrukcja (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c62eae57ae127fcbb860fe72853604802cccd9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referencje i importy — Instrukcja (Visual Basic)
Można udostępnić obiektów zewnętrznych do projektu, wybierając **Dodaj odwołanie** na **projektu** menu. Odwołania w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] może wskazywać na zestawy, które są takie jak biblioteki typów, ale zawierają więcej informacji.  
  
## <a name="the-imports-statement"></a>Importy — instrukcja  
 Zestawy zawiera jeden lub kilka przestrzeni nazw. Podczas dodawania odwołania do zestawu, możesz także dodać `Imports` instrukcji, aby moduł, który określa widoczność nazw tego zestawu w module. `Imports` Instrukcji zapewnia zakresu kontekstu, która umożliwia używanie tylko części obszaru nazw, które są niezbędne do dostarczania unikatowe odwołanie.  
  
 `Imports` Instrukcji ma następującą składnię:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`odnosi się do krótkiej nazwy, używanych w ramach kodu do odwoływania się do importowanych przestrzeni nazw. `Namespace`jest dostępna za pośrednictwem jednej przestrzeni nazw odwołanie do projektu, za pośrednictwem definicji w projekcie, lub poprzedniej `Imports` instrukcji.  
  
 Moduł może zawierać dowolną liczbę `Imports` instrukcje. Muszą występować po jednej `Option` instrukcje, jeśli nie istnieje, ale przed innymi kodu.  
  
> [!NOTE]
>  Nie należy mylić odwołania do projektu z `Imports` instrukcji lub `Declare` instrukcji. Odwołania do projektu udostępnić zewnętrznych obiektów, takich jak obiekty w zestawach, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektów. `Imports` Instrukcja jest używane w celu uproszczenia dostępu do odwołania do projektu, ale nie zapewnia dostępu do tych obiektów. `Declare` Instrukcji służy do deklarowania odwołanie do zewnętrznej procedury biblioteki dołączanej (dynamicznie DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Aliasy użycia z Importy — instrukcja  
 `Imports` Instrukcji ułatwia metody dostępu do klasy, eliminując konieczność jawnie wpisz w pełni kwalifikowane nazwy odwołań. Aliasy umożliwiają przypisać nazwę służący do tylko jednej części obszaru nazw. Na przykład sekwencji, który powoduje, że jeden fragment tekstu do wyświetlenia w wielu wierszach CR/LF jest częścią <xref:Microsoft.VisualBasic.ControlChars> modułu w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. Aby użyć tego stała w programie bez aliasu, konieczne będzie wpisz następujący kod:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`instrukcje musi być zawsze pierwszych wierszy bezpośrednio po żadnego `Option` instrukcji w module. Poniższy fragment kodu przedstawia sposób importowania i przypisać aliasu <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modułu:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Odwołania do tej przestrzeni nazw może być znacznie krótszy:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Jeśli `Imports` instrukcji nie zawiera nazwę aliasu, elementy zdefiniowane w importowanych przestrzeni nazw może być używany w module bez kwalifikacji. Jeśli zostanie określona nazwa aliasu, należy użyć jako kwalifikator dla nazw zawartych w tej przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Instrukcje: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
