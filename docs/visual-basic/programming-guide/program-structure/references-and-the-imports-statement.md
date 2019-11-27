---
title: Referencje i instrukcja Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347277"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referencje i importy — Instrukcja (Visual Basic)
Obiekty zewnętrzne można udostępnić projekt, wybierając polecenie **Dodaj odwołanie** w menu **projekt** . Odwołania w Visual Basic mogą wskazywać zestawy, które są takie jak biblioteki typów, ale zawierają więcej informacji.  
  
## <a name="the-imports-statement"></a>Instrukcja Imports  
 Zestawy obejmują co najmniej jedną przestrzeń nazw. Po dodaniu odwołania do zestawu, można również dodać instrukcję `Imports` do modułu, który kontroluje widoczność przestrzeni nazw tego zestawu w module. Instrukcja `Imports` zawiera kontekst zakresu, który umożliwia użycie tylko części przestrzeni nazw niezbędnej do dostarczenia unikatowego odwołania.  
  
 Instrukcja `Imports` ma następującą składnię:  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` odnosi się do krótkiej nazwy, której można użyć w kodzie, aby odwołać się do zaimportowanej przestrzeni nazw. `Namespace` jest przestrzenią nazw dostępną za pomocą odwołania do projektu, za pomocą definicji w ramach projektu lub poprzedniej instrukcji `Imports`.  
  
 Moduł może zawierać dowolną liczbę instrukcji `Imports`. Muszą one znajdować się po każdej instrukcji `Option`, jeśli są obecne, ale przed jakimkolwiek innym kodem.  
  
> [!NOTE]
> Nie należy mylić odwołań do projektu za pomocą instrukcji `Imports` ani instrukcji `Declare`. Odwołania projektu tworzą obiekty zewnętrzne, takie jak obiekty w zestawach, dostępne do Visual Basic projektów. Instrukcja `Imports` służy do uproszczenia dostępu do odwołań do projektu, ale nie zapewnia dostępu do tych obiektów. Instrukcja `Declare` służy do deklarowania odwołania do procedury zewnętrznej w bibliotece dołączanej dynamicznie (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Używanie aliasów z instrukcją Imports  
 Instrukcja `Imports` ułatwia uzyskiwanie dostępu do metod klas przez wyeliminowanie konieczności jawnego wpisywania w pełni kwalifikowanych nazw odwołań. Aliasy umożliwiają przypisanie nazwy bardziej przyjaznej tylko do jednej części przestrzeni nazw. Na przykład sekwencja powrotu karetki i wysuwu wiersza, która powoduje, że pojedynczy fragment tekstu, który ma być wyświetlany w wielu wierszach, jest częścią modułu <xref:Microsoft.VisualBasic.ControlChars> w przestrzeni nazw <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. Aby użyć tej stałej w programie bez aliasu, należy wpisać następujący kod:  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 instrukcje `Imports` muszą zawsze być pierwszym wierszem bezpośrednio po dowolnych instrukcjach `Option` w module. Poniższy fragment kodu przedstawia sposób importowania i przypisywania aliasu do modułu <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>:  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Przyszłe odwołania do tej przestrzeni nazw mogą być znacznie krótsze:  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 Jeśli instrukcja `Imports` nie zawiera nazwy aliasu, elementy zdefiniowane w zaimportowanym obszarze nazw mogą być używane w module bez kwalifikacji. Jeśli Nazwa aliasu jest określona, musi być używana jako kwalifikator dla nazw zawartych w tej przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Przestrzenie nazw w Visual Basic](namespaces.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
