---
title: Przestrzenie nazw
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 087c6f02e1fca9cf2664ca76581c08a9b1a5e447
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398360"
---
# <a name="namespaces-in-visual-basic"></a>Przestrzenie nazw w Visual Basic
Przestrzenie nazw organizują obiekty zdefiniowane w zestawie. Zestawy mogą zawierać wiele przestrzeni nazw, które mogą z kolei zawierać inne przestrzenie nazw. Przestrzenie nazw uniemożliwiają niejednoznaczność i upraszczają odwołania w przypadku używania dużych grup obiektów, takich jak biblioteki klas.  
  
 Na przykład .NET Framework definiuje <xref:System.Windows.Forms.ListBox> klasę w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw. Poniższy fragment kodu przedstawia sposób deklarowania zmiennej przy użyciu w pełni kwalifikowanej nazwy dla tej klasy:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Unikanie kolizji nazw  
 Przestrzenie nazw .NET Framework rozwiązaniu problemu czasami nazywanego *zanieczyszczeniem przestrzeni nazw*, w którym deweloper biblioteki klas jest niehamowany przez użycie podobnych nazw w innej bibliotece. Te konflikty z istniejącymi składnikami są czasami nazywane *kolizjami nazw*.  
  
 Na przykład jeśli utworzysz nową klasę o nazwie, możesz `ListBox` jej użyć w projekcie bez kwalifikacji. Jeśli jednak chcesz użyć <xref:System.Windows.Forms.ListBox> klasy .NET Framework w tym samym projekcie, musisz użyć w pełni kwalifikowanego odwołania, aby odwołać odwołanie. Jeśli odwołanie nie jest unikatowe, Visual Basic generuje błąd informujący o tym, że nazwa jest niejednoznaczna. Poniższy przykład kodu demonstruje, jak zadeklarować te obiekty:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Na poniższej ilustracji przedstawiono dwie hierarchie przestrzeni nazw, które zawierają obiekt o nazwie `ListBox` :  
  
 ![Zrzut ekranu pokazujący dwie hierarchie przestrzeni nazw.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Domyślnie każdy plik wykonywalny tworzony za pomocą Visual Basic zawiera przestrzeń nazw o tej samej nazwie co projekt. Na przykład, jeśli zdefiniujesz obiekt w projekcie o nazwie `ListBoxProject` , plik wykonywalny ListBoxProject. exe zawiera przestrzeń nazw o nazwie `ListBoxProject` .  
  
 Wiele zestawów może używać tej samej przestrzeni nazw. Visual Basic traktuje je jako pojedynczy zestaw nazw. Na przykład można zdefiniować klasy dla przestrzeni nazw o nazwie `SomeNameSpace` w zestawie o nazwie `Assemb1` i zdefiniować dodatkowe klasy dla tej samej przestrzeni nazw z zestawu o nazwie `Assemb2` .  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 W pełni kwalifikowane nazwy są odwołaniami do obiektów, które są poprzedzone nazwą przestrzeni nazw, w której jest zdefiniowany obiekt. Możesz użyć obiektów zdefiniowanych w innych projektach, jeśli utworzysz odwołanie do klasy (wybierając **Dodaj odwołanie** z menu **projekt** ), a następnie użyj w pełni kwalifikowanej nazwy dla obiektu w kodzie. Poniższy fragment kodu pokazuje, jak używać w pełni kwalifikowanej nazwy dla obiektu z przestrzeni nazw innego projektu:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 W pełni kwalifikowane nazwy uniemożliwiają konflikty nazw, ponieważ umożliwiają kompilatorowi określenie, który obiekt jest używany. Nazwy same mogą jednak być długie i nieskomplikowane. Aby to zrobić, można użyć `Imports` instrukcji w celu zdefiniowania *aliasu*— skróconej nazwy, której można użyć zamiast w pełni kwalifikowanej nazwy. Poniższy przykład kodu tworzy aliasy dla dwóch w pełni kwalifikowanych nazw i używa tych aliasów do definiowania dwóch obiektów.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Jeśli używasz `Imports` instrukcji bez aliasu, możesz użyć wszystkich nazw w tej przestrzeni nazw bez kwalifikacji, pod warunkiem, że są one unikatowe dla projektu. Jeśli projekt zawiera `Imports` instrukcje dla przestrzeni nazw, które zawierają elementy o tej samej nazwie, należy w pełni zakwalifikować tę nazwę podczas korzystania z niej. Załóżmy na przykład, że projekt zawiera następujące dwie `Imports` instrukcje:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Jeśli próba użycia nie zostanie w `Class1` pełni zakwalifikowania, Visual Basic generuje błąd informujący o tym, że nazwa `Class1` jest niejednoznaczna.  
  
## <a name="namespace-level-statements"></a>Instrukcje na poziomie przestrzeni nazw  
 W przestrzeni nazw można definiować elementy, takie jak moduły, interfejsy, klasy, Delegaty, wyliczenia, struktury i inne przestrzenie nazw. Nie można definiować elementów, takich jak właściwości, procedury, zmienne i zdarzenia, na poziomie przestrzeni nazw. Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Globalne słowo kluczowe w w pełni kwalifikowanych nazwach  
 Jeśli zdefiniowano hierarchię zagnieżdżoną przestrzeni nazw, kod wewnątrz tej hierarchii może mieć zablokowany dostęp do <xref:System?displayProperty=nameWithType> przestrzeni nazw .NET Framework. Poniższy przykład ilustruje hierarchię, w której `SpecialSpace.System` przestrzeń nazw blokuje dostęp do <xref:System?displayProperty=nameWithType> .  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 W związku z tym kompilator Visual Basic nie może pomyślnie rozpoznać odwołania do <xref:System.Int32?displayProperty=nameWithType> , ponieważ nie `SpecialSpace.System` definiuje `Int32` . Możesz użyć `Global` słowa kluczowego do uruchomienia łańcucha kwalifikacji na najbardziej zewnętrznym poziomie biblioteki klas .NET Framework. Pozwala to określić <xref:System?displayProperty=nameWithType> przestrzeń nazw lub inną przestrzeń nazw w bibliotece klas. Ilustruje to poniższy przykład.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Można użyć, `Global` Aby uzyskać dostęp do innych obszarów nazw na poziomie głównym, takich jak <xref:Microsoft.VisualBasic?displayProperty=nameWithType> i wszystkich przestrzeni nazw skojarzonych z projektem.  
  
## <a name="global-keyword-in-namespace-statements"></a>Globalne słowo kluczowe w instrukcjach Namespace  
 Możesz również użyć `Global` słowa kluczowego w [instrukcji Namespace](../../language-reference/statements/namespace-statement.md). Pozwala to definiować przestrzeń nazw poza główną przestrzenią nazw projektu.  
  
 Wszystkie przestrzenie nazw w projekcie są oparte na głównej przestrzeni nazw dla projektu.  Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie. Na przykład jeśli projekt ma nazwę `ConsoleApplication1` , jego elementy programistyczne należą do przestrzeni nazw `ConsoleApplication1` . Jeśli zadeklarujesz `Namespace Magnetosphere` , odwołania do `Magnetosphere` w projekcie będą miały dostęp `ConsoleApplication1.Magnetosphere` .  
  
 W poniższych przykładach użyto `Global` słowa kluczowego, aby zadeklarować przestrzeń nazw poza główną przestrzeń nazw dla projektu.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 W deklaracji przestrzeni nazw `Global` nie może być zagnieżdżona w innej przestrzeni nazw.  
  
 Za pomocą [strony aplikacji, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) można wyświetlać i modyfikować **główną przestrzeń nazw** projektu.  W przypadku nowych projektów, **główna przestrzeń nazw** domyślnie jest nazwą projektu. Aby `Global` można było uzyskać przestrzeń nazw najwyższego poziomu, można wyczyścić wpis **głównej przestrzeni nazw** , aby pole było puste. Czyszczenie **głównej przestrzeni nazw** usuwa potrzebę `Global` słowa kluczowego w deklaracjach przestrzeni nazw.  
  
 Jeśli `Namespace` instrukcja deklaruje nazwę, która jest również przestrzenią nazw w .NET Framework, przestrzeń nazw .NET Framework będzie niedostępna, jeśli `Global` słowo kluczowe nie zostanie użyte w w pełni kwalifikowanej nazwie. Aby umożliwić dostęp do tego .NET Framework przestrzeni nazw bez użycia `Global` słowa kluczowego, można dołączyć `Global` słowo kluczowe do `Namespace` instrukcji.  
  
 Poniższy przykład zawiera `Global` słowo kluczowe w `System.Text` deklaracji przestrzeni nazw.  
  
 Jeśli `Global` słowo kluczowe nie było obecne w deklaracji przestrzeni nazw, nie można <xref:System.Text.StringBuilder> uzyskać do niego dostępu bez określenia `Global.System.Text.StringBuilder` . Dla projektu o nazwie `ConsoleApplication1` odwołuje się do `System.Text` niego, `ConsoleApplication1.System.Text` Jeśli `Global` słowo kluczowe nie zostało użyte.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Referencje i instrukcja Imports](references-and-the-imports-statement.md)
- [Imports — Instrukcja (.NET Namespace i Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Pisanie kodu dla rozwiązań pakietu Office](/visualstudio/vsto/writing-code-in-office-solutions)
