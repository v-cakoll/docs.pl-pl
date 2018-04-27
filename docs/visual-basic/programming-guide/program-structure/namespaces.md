---
title: Przestrzenie nazw w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ec038a17b4a6b10dbe339fe33969c4ade57e2a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="namespaces-in-visual-basic"></a>Przestrzenie nazw w Visual Basic
Przestrzenie nazw organizowanie obiektów zdefiniowanych w zestawie. Zestawy może zawierać wiele obszarów nazw, który z kolei może zawierać innych przestrzeniach nazw. Przestrzenie nazw uniknąć niejednoznaczności i uprościć odwołań w przypadku przy użyciu dużych grup obiektów, takich jak biblioteki klas.  
  
 Na przykład [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definiuje <xref:System.Windows.Forms.ListBox> klasy w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw. Poniższy fragment kodu przedstawia sposób zadeklarować zmiennej przy użyciu w pełni kwalifikowana nazwa dla tej klasy:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Unikanie konfliktów nazw  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] przestrzenie nazw rozwiązać problem czasami nazywane *zanieczyszczenie przestrzeni nazw*, w którym dewelopera biblioteki klas jest utrudniona przez stosowanie podobnych nazw w innej bibliotece. Te konflikty z istniejącymi elementami są nazywane *kolizji nazw*.  
  
 Na przykład, jeśli tworzysz nową klasę o nazwie `ListBox`, może być używany w projekcie bez kwalifikacji. Jednak jeśli chcesz użyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> klasy w tym samym projekcie, aby odnieść unikatowy należy użyć pełni kwalifikowane odwołanie. Jeśli odwołanie nie jest unikatowa, Visual Basic generuje komunikat o błędzie informujący, że nazwa jest niejednoznaczna. Poniższy przykładowy kod przedstawia sposób zadeklarować tych obiektów:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 Na poniższej ilustracji przedstawiono dwie hierarchie przestrzeni nazw, w obu zawierający obiekt o nazwie `ListBox`.  
  
 ![Hierarchia Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Domyślnie każdy plik wykonywalny, utworzone przy użyciu języka Visual Basic zawiera obszarze nazw o nazwie identycznej z nazwą projektu. Na przykład, jeśli zdefiniowania obiektu, w ramach projektu o nazwie `ListBoxProject`, plik wykonywalny ListBoxProject.exe zawiera obszar nazw o nazwie `ListBoxProject`.  
  
 Wiele zestawów można użyć tego samego obszaru nazw. Visual Basic traktowane jako pojedynczy zestaw nazw. Na przykład można zdefiniować klasy dla przestrzeni nazw o nazwie `SomeNameSpace` w zestawie o nazwie `Assemb1`i zdefiniować dodatkowe klasy dla tego samego obszaru nazw z zestawu o nazwie `Assemb2`.  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 W pełni kwalifikowane nazwy są odwołania do obiektów, które są poprzedzane prefiksem nazwy przestrzeni nazw, w którym zdefiniowana jest obiekt. Można użyć obiektów zdefiniowanych w innych projektach, jeśli utworzono odwołanie do klasy (przez wybranie **Dodaj odwołanie** z **projektu** menu), a następnie użyj w pełni kwalifikowana nazwa obiektu w kodzie. Poniższy fragment kodu przedstawia sposób użycia w pełni kwalifikowana nazwa obiektu z innego projektu przestrzeni nazw:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 W pełni kwalifikowane nazwy zapobiec nazw powoduje konflikt, ponieważ są one umożliwiać kompilator, aby określić obiektu, który jest w użyciu. Jednak nazwy można uzyskać długich i skomplikowane. Aby uzyskać obejścia tego problemu, można użyć `Imports` instrukcji, aby zdefiniować *alias*— skróconą nazwę można użyć zamiast w pełni kwalifikowana nazwa. Na przykład poniższy przykład kodu tworzy aliasów dla dwóch w pełni kwalifikowane nazwy i używa tych aliasy, aby zdefiniować dwa obiekty.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Jeśli używasz `Imports` instrukcji bez aliasu, można używać wszystkich nazw w tej przestrzeni nazw bez kwalifikacji, podane, są one unikatowe do projektu. Jeśli projekt zawiera `Imports` instrukcje dla przestrzeni nazw, która zawiera elementy o takiej samej nazwie, użytkownik musi pełnej nazwy tego przypadku użycia jej. Załóżmy na przykład projekt zawiera dwa `Imports` instrukcji:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Jeśli próba użycia `Class1` bez pełni kwalifikujące go, Visual Basic generuje komunikat o błędzie informujący, że nazwa `Class1` jest niejednoznaczna.  
  
## <a name="namespace-level-statements"></a>Poziom Namespace — instrukcje  
 W obszarze nazw należy zdefiniować elementy, takie jak moduły, interfejsów, klas, obiektów delegowanych, wyliczeń, struktur i innych przestrzeniach nazw. Nie można zdefiniować elementy, takie jak właściwości, procedur, zmiennych i zdarzenia na poziomie przestrzeni nazw. Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Global — słowo kluczowe w pełni kwalifikowane nazwy  
 Jeśli zdefiniowano hierarchii zagnieżdżonych obszarów nazw kodu wewnątrz tej hierarchii może zostać zablokowany dostęp do <xref:System?displayProperty=nameWithType> przestrzeni nazw programu .NET Framework. Poniższy przykład przedstawia hierarchię, w którym `SpecialSpace.System` przestrzeni nazw zablokuje dostęp do <xref:System?displayProperty=nameWithType>.  
  
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
  
 W związku z tym kompilator Visual Basic nie można rozpoznać odwołania do <xref:System.Int32?displayProperty=nameWithType>, ponieważ `SpecialSpace.System` nie definiuje `Int32`. Można użyć `Global` — słowo kluczowe, aby uruchomić łańcucha kwalifikacji na poziomie najbardziej zewnętrznego w bibliotece klas programu .NET Framework. Dzięki temu można określić <xref:System?displayProperty=nameWithType> przestrzeni nazw lub innych przestrzeni nazw w bibliotece klas. Ilustruje to poniższy przykład.  
  
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
  
 Można użyć `Global` można uzyskać dostępu do innych przestrzeniach nazw poziomu głównego, takich jak <xref:Microsoft.VisualBasic?displayProperty=nameWithType>i skojarzone z projektu przestrzeni nazw.  
  
## <a name="global-keyword-in-namespace-statements"></a>Global — słowo kluczowe w instrukcjach "Namespace"  
 Można również użyć `Global` — słowo kluczowe w [instrukcji Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). Dzięki temu można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu.  
  
 Wszystkie przestrzenie nazw w projekcie są oparte na przestrzeń nazw korzenia dla projektu.  Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie.  Na przykład jeśli projekt nosi nazwę `ConsoleApplication1`, jego elementy programistyczne należą do przestrzeni nazw `ConsoleApplication1`. W przypadku `Namespace Magnetosphere`, odwołuje się do `Magnetosphere` w projekcie będą uzyskiwać dostęp do `ConsoleApplication1.Magnetosphere`.  
  
 W poniższych przykładach użyto `Global` — słowo kluczowe, aby zadeklarować przestrzeni nazw poza głównej przestrzeni nazw dla projektu.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 W deklaracji przestrzeni nazw `Global` nie mogą być zagnieżdżone w innej przestrzeni nazw.  
  
 Można użyć [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) do wyświetlania i modyfikowania **Namespace głównego** projektu.  Dla nowych projektów **Namespace głównego** domyślnie nazwa projektu. Powoduje `Global` się przestrzeni nazw najwyższego poziomu, można wyczyścić **Namespace głównego** wpis tak, że pole jest puste. Wyczyszczenie **Namespace głównego** eliminuje to potrzebę `Global` — słowo kluczowe w deklaracjach przestrzeni nazw.  
  
 Jeśli `Namespace` instrukcji deklaruje nazwę, która jest również przestrzeni nazw w programie .NET Framework, obszaru nazw .NET Framework jest niedostępny Jeśli `Global` — słowo kluczowe nie jest używany w pełni kwalifikowanej nazwy. Aby umożliwić dostęp do tego obszaru nazw .NET Framework bez użycia `Global` — słowo kluczowe, mogą obejmować `Global` — słowo kluczowe w `Namespace` instrukcji.  
  
 W poniższym przykładzie przedstawiono `Global` — słowo kluczowe w `System.Text` deklaracji przestrzeni nazw.  
  
 Jeśli `Global` — słowo kluczowe nie była obecna w deklaracji przestrzeni nazw <xref:System.Text.StringBuilder> nie było możliwe bez określania `Global.System.Text.StringBuilder`. Dla projektu o nazwie `ConsoleApplication1`, odwołuje się do `System.Text` może uzyskać dostępu do `ConsoleApplication1.System.Text` Jeśli `Global` nie użyto słowa kluczowego.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Instrukcje: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Pisanie kodu dla rozwiązań pakietu Office](https://msdn.microsoft.com/library/bb608596)
