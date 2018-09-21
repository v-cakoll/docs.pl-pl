---
title: Przestrzenie nazw w Visual Basic
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
ms.openlocfilehash: 6b320d21c33fa798ca2fd3ef5a04363d141f99f2
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525529"
---
# <a name="namespaces-in-visual-basic"></a>Przestrzenie nazw w Visual Basic
Przestrzenie nazw organizują obiekty zdefiniowane w zestawie. Zespoły mogą zawierać wiele przestrzeni nazw, który z kolei może zawierać innych przestrzeniach nazw. Przestrzenie nazw uniknąć niejednoznaczności i uprościć odwołania, korzystając z dużych grup obiektów, takich jak biblioteki klas.  
  
 Na przykład [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definiuje <xref:System.Windows.Forms.ListBox> klasy w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw. Poniższy fragment kodu pokazuje sposób deklarowania zmiennej za pomocą w pełni kwalifikowana nazwa dla tej klasy:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Unikanie konfliktów nazw  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] przestrzenie nazw rozwiązać problem, czasami nazywane *zanieczyszczenie przestrzeni nazw*, w której Deweloper biblioteki klas dostęp utrudniają przy użyciu podobnych nazwach w innej bibliotece. Te konflikty z istniejącymi elementami są czasami nazywane *Kolizje nazw*.  
  
 Na przykład, jeśli tworzysz nową klasę o nazwie `ListBox`, można go użyć wewnątrz projektu bez kwalifikacji. Jednakże jeśli chcesz używać [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> klasy w tym samym projekcie, należy użyć w pełni kwalifikowane odwołanie unikatowość odwołania. Jeśli odwołanie nie jest unikatowa, Visual Basic generuje komunikat o błędzie informujący, że nazwa jest niejednoznaczna. Poniższy przykład kodu pokazuje sposób deklarowania tych obiektów:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 Na poniższej ilustracji przedstawiono dwie hierarchie przestrzeni nazw, w obu zawierającą obiekt o nazwie `ListBox`.  
  
 ![Hierarchia Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Domyślnie co plik wykonywalny, utworzonej za pomocą Visual Basic zawiera przestrzeń nazw o takiej samej nazwie co projekt. Na przykład, jeśli zdefiniujesz obiekt w ramach projektu o nazwie `ListBoxProject`, plik wykonywalny ListBoxProject.exe zawiera przestrzeń nazw o nazwie `ListBoxProject`.  
  
 Wiele zestawów, można użyć tej samej przestrzeni nazw. Visual Basic traktuje je jako pojedynczy zestaw nazw. Na przykład można zdefiniować klasy w przestrzeni nazw o nazwie `SomeNameSpace` w zestawie o nazwie `Assemb1`i zdefiniować dodatkowe klasy dla tej samej przestrzeni nazw z zestawu o nazwie `Assemb2`.  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 W pełni kwalifikowane nazwy są odwołania do obiektów, które są poprzedzone nazwą przestrzeni nazw, w którym jest zdefiniowany obiekt. Można użyć obiektów zdefiniowanych w innych projektach, jeśli tworzysz odwołanie do klasy (wybierając **Dodaj odwołanie** z **projektu** menu), a następnie użyć w pełni kwalifikowana nazwa obiektu w kodzie. Poniższy fragment kodu przedstawia sposób używania w pełni kwalifikowana nazwa obiektu z innego projektu w przestrzeni nazw:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 W pełni kwalifikowanych nazw zapobiec nazw powoduje konflikt, ponieważ umożliwiają one programowi, aby kompilator mógł określić obiektu, który jest używany. Jednak same nazwy, można uzyskać długich i kłopotliwe. Aby obejść ten problem, można użyć `Imports` instrukcji, aby zdefiniować *alias*— skrócona nazwa, można użyć zamiast w pełni kwalifikowana nazwa. Na przykład poniższy kod tworzy aliasy dla dwóch w pełni kwalifikowanych nazw i używa te aliasy, aby zdefiniować dwa obiekty.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Jeśli używasz `Imports` instrukcji bez aliasu, można użyć wszystkich nazw w tej przestrzeni nazw bez kwalifikacji, podane są unikatowe dla projektu. Jeśli projekt zawiera `Imports` instrukcji dla przestrzeni nazw, które zawierają elementy o takiej samej nazwie, muszą w pełni kwalifikujesz się do tej nazwy wykorzystane moce. Załóżmy na przykład projekt zawiera dwie poniższe `Imports` instrukcji:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Jeśli spróbujesz użyć `Class1` bez w pełni kwalifikowania go, Visual Basic generuje komunikat o błędzie informujący, że nazwa `Class1` jest niejednoznaczna.  
  
## <a name="namespace-level-statements"></a>Poziom Namespace instrukcji  
 W przestrzeni nazw można zdefiniować elementy, takie jak moduły, interfejsy, klasy, delegatów, wyliczenia, struktur i inne przestrzenie nazw. Nie można zdefiniować elementy, takie jak właściwości, procedur, zmienne i zdarzenia na poziomie przestrzeni nazw. Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Global — słowo kluczowe w pełni kwalifikowane nazwy  
 Jeśli zdefiniowano hierarchię zagnieżdżoną przestrzenie nazw, kod wewnątrz tej hierarchii mogą mieć zablokowany dostęp do <xref:System?displayProperty=nameWithType> przestrzeni nazw programu .NET Framework. Poniższy przykład ilustruje, hierarchię, w którym `SpecialSpace.System` przestrzeni nazw powoduje zablokowanie dostępu do <xref:System?displayProperty=nameWithType>.  
  
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
  
 Co w efekcie kompilator Visual Basic nie można pomyślnie rozpoznać odwołania do <xref:System.Int32?displayProperty=nameWithType>, ponieważ `SpecialSpace.System` nie definiuje `Int32`. Możesz użyć `Global` — słowo kluczowe, można uruchomić w łańcuchu kwalifikacji na poziomie najbardziej zewnętrznej biblioteki klas .NET Framework. Dzięki temu można określić <xref:System?displayProperty=nameWithType> przestrzeni nazw lub innych przestrzeni nazw w bibliotece klas. Ilustruje to poniższy przykład.  
  
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
  
 Możesz użyć `Global` do dostępu do innych obszarów nazw do poziomu głównego, takich jak <xref:Microsoft.VisualBasic?displayProperty=nameWithType>i dowolnego obszaru nazw skojarzonej z projektem.  
  
## <a name="global-keyword-in-namespace-statements"></a>Global — słowo kluczowe w instrukcjach Namespace  
 Można również użyć `Global` — słowo kluczowe w [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md). Dzięki temu można zdefiniować obszar nazw poza głównej przestrzeni nazw projektu.  
  
 Wszystkie przestrzenie nazw w projekcie opierają się na przestrzeń nazw korzenia dla projektu.  Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie.  Na przykład jeśli projekt nosi nazwę `ConsoleApplication1`, jego elementy programistyczne należą do przestrzeni nazw `ConsoleApplication1`. Jeśli zadeklarujesz `Namespace Magnetosphere`, odwołuje się do `Magnetosphere` w projekcie będą miały dostęp `ConsoleApplication1.Magnetosphere`.  
  
 W poniższych przykładach używane `Global` — słowo kluczowe do deklarowania, przestrzeń nazw z głównej przestrzeni nazw dla projektu.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 W deklaracji przestrzeni nazw `Global` nie może być zagnieżdżona w innej przestrzeni nazw.  
  
 Możesz użyć [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) wyświetlać i modyfikować **Namespace głównego** projektu.  Dla nowych projektów **Namespace głównego** domyślnie ustawiana na nazwę projektu. Aby spowodować `Global` jako przestrzeń nazw najwyższego poziomu, można wyczyścić **Namespace głównego** wpis tak, że pole jest puste. Czyszczenie **Namespace głównego** eliminuje potrzebę `Global` — słowo kluczowe w deklaracji przestrzeni nazw.  
  
 Jeśli `Namespace` instrukcja deklaruje nazwę, która jest również przestrzeni nazw w programie .NET Framework, obszaru nazw .NET Framework staje się niedostępny Jeśli `Global` — słowo kluczowe nie jest używany w pełni kwalifikowanej nazwy. Aby umożliwić dostęp do tego obszaru nazw .NET Framework bez użycia `Global` — słowo kluczowe, mogą obejmować `Global` — słowo kluczowe w `Namespace` instrukcji.  
  
 W poniższym przykładzie przedstawiono `Global` — słowo kluczowe w `System.Text` deklarację przestrzeni nazw.  
  
 Jeśli `Global` — słowo kluczowe nie była obecna w deklaracji przestrzeni nazw <xref:System.Text.StringBuilder> nie jest dostępna bez określania `Global.System.Text.StringBuilder`. Dla projektu o nazwie `ConsoleApplication1`, odwołuje się do `System.Text` dostęp do `ConsoleApplication1.System.Text` Jeśli `Global` nie użyto słowa kluczowego.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListBox>  
- <xref:System.Windows.Forms?displayProperty=nameWithType>  
- [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Instrukcje: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [Pisanie kodu dla rozwiązań pakietu Office](/visualstudio/vsto/writing-code-in-office-solutions)
