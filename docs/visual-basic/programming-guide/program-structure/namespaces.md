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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400674"
---
# <a name="namespaces-in-visual-basic"></a>Przestrzenie nazw w Visual Basic
Przestrzenie nazw organizują obiekty zdefiniowane w złożeniu. Zestawy mogą zawierać wiele obszarów nazw, które z kolei mogą zawierać inne przestrzenie nazw. Przestrzenie nazw zapobiegają niejednoznaczności i upraszczają odwołania podczas korzystania z dużych grup obiektów, takich jak biblioteki klas.  
  
 Na przykład .NET Framework definiuje <xref:System.Windows.Forms.ListBox> klasę <xref:System.Windows.Forms?displayProperty=nameWithType> w obszarze nazw. Poniższy fragment kodu pokazuje, jak zadeklarować zmienną przy użyciu w pełni kwalifikowanej nazwy dla tej klasy:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Unikanie kolizji nazw  
 .NET Framework przestrzenie nazw rozwiązać problem czasami nazywany *zanieczyszczenia obszaru nazw,* w którym deweloper biblioteki klas jest utrudniony przez użycie podobnych nazw w innej bibliotece. Te konflikty z istniejącymi komponentami są czasami nazywane *kolizjami nazw*.  
  
 Na przykład jeśli utworzysz `ListBox`nową klasę o nazwie , można jej używać wewnątrz projektu bez kwalifikacji. Jednak jeśli chcesz użyć klasy .NET Framework <xref:System.Windows.Forms.ListBox> w tym samym projekcie, należy użyć w pełni kwalifikowanego odwołania, aby odwołanie było unikatowe. Jeśli odwołanie nie jest unikatowe, visual basic generuje błąd stwierdzający, że nazwa jest niejednoznaczna. Poniższy przykład kodu pokazuje, jak zadeklarować te obiekty:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Na poniższej ilustracji przedstawiono dwie hierarchie `ListBox`obszarów nazw, oba zawierające obiekt o nazwie:  
  
 ![Zrzut ekranu przedstawiający dwie hierarchie obszaru nazw.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Domyślnie każdy plik wykonywalny utworzony za pomocą języka Visual Basic zawiera obszar nazw o takiej samej nazwie jak projekt. Na przykład, jeśli zdefiniujesz `ListBoxProject`obiekt w projekcie o nazwie , plik wykonywalny ListBoxProject.exe zawiera obszar nazw o nazwie `ListBoxProject`.  
  
 Wiele zestawów można użyć tego samego obszaru nazw. Visual Basic traktuje je jako pojedynczy zestaw nazw. Na przykład można zdefiniować klasy dla `SomeNameSpace` obszaru nazw `Assemb1`wywoływanego w zestawie o nazwie i `Assemb2`zdefiniować dodatkowe klasy dla tego samego obszaru nazw z zestawu o nazwie .  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 W pełni kwalifikowane nazwy to odwołania do obiektów, które są poprzedzone nazwą obszaru nazw, w którym obiekt jest zdefiniowany. Można użyć obiektów zdefiniowanych w innych projektach, jeśli utworzysz odwołanie do klasy (wybierając **dodaj odwołanie** z menu **Projekt),** a następnie użyj w pełni kwalifikowanej nazwy obiektu w kodzie. Poniższy fragment kodu pokazuje, jak używać w pełni kwalifikowanej nazwy obiektu z obszaru nazw innego projektu:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 W pełni kwalifikowane nazwy zapobiegają konfliktom nazewnictwa, ponieważ umożliwiają kompilatorowi określenie, który obiekt jest używany. Jednak same nazwy mogą stać się długie i uciążliwe. Aby obejść ten problem, `Imports` można użyć instrukcji do zdefiniowania *aliasu*— skróconej nazwy, której można użyć zamiast w pełni kwalifikowanej nazwy. Na przykład poniższy przykład kodu tworzy aliasy dla dwóch w pełni kwalifikowanych nazw i używa tych aliasów do definiowania dwóch obiektów.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Jeśli używasz `Imports` instrukcji bez aliasu, można użyć wszystkich nazw w tym obszarze nazw bez kwalifikacji, pod warunkiem, że są unikatowe dla projektu. Jeśli projekt `Imports` zawiera instrukcje dla obszarów nazw, które zawierają elementy o tej samej nazwie, należy w pełni zakwalifikować tę nazwę podczas korzystania z niej. Załóżmy, że na przykład projekt `Imports` zawierał następujące dwie instrukcje:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Jeśli spróbujesz `Class1` użyć bez pełnego zakwalifikowania go, Visual Basic `Class1` generuje błąd stwierdzający, że nazwa jest niejednoznaczna.  
  
## <a name="namespace-level-statements"></a>Instrukcje poziomu obszaru nazw  
 W obszarze nazw można definiować elementy, takie jak moduły, interfejsy, klasy, delegatów, wyliczenia, struktury i inne przestrzenie nazw. Nie można definiować elementów, takich jak właściwości, procedury, zmienne i zdarzenia na poziomie obszaru nazw. Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Globalne słowo kluczowe w pełni kwalifikowanych nazwach  
 Jeśli zdefiniowano zagnieżdżoną hierarchię obszarów nazw, kod wewnątrz tej <xref:System?displayProperty=nameWithType> hierarchii może być zablokowany w dostępie do obszaru nazw programu .NET Framework. Poniższy przykład ilustruje hierarchię, `SpecialSpace.System` w której <xref:System?displayProperty=nameWithType>obszar nazw blokuje dostęp do .  
  
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
  
 W rezultacie kompilator języka Visual Basic nie <xref:System.Int32?displayProperty=nameWithType>może `SpecialSpace.System` pomyślnie `Int32`rozpoznać odwołania do programu , ponieważ nie definiuje . Za pomocą `Global` słowa kluczowego można uruchomić łańcuch kwalifikacji na najbardziej wysuniętym na zewnątrz poziomie biblioteki klas .NET Framework. Dzięki temu można <xref:System?displayProperty=nameWithType> określić obszar nazw lub inny obszar nazw w bibliotece klas. Ilustruje to poniższy przykład.  
  
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
  
 Można użyć `Global` dostępu do innych głównych obszarów <xref:Microsoft.VisualBasic?displayProperty=nameWithType>nazw na poziomie, takich jak , i dowolnej przestrzeni nazw skojarzonej z projektem.  
  
## <a name="global-keyword-in-namespace-statements"></a>Globalne słowo kluczowe w instrukcjach obszaru nazw  
 Słowa kluczowego `Global` można również użyć w [instrukcji Obszar nazw](../../../visual-basic/language-reference/statements/namespace-statement.md). Dzięki temu można zdefiniować obszar nazw z głównej przestrzeni nazw projektu.  
  
 Wszystkie przestrzenie nazw w projekcie są oparte na głównej przestrzeni nazw projektu.  Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie. Na przykład, jeśli projekt `ConsoleApplication1`ma nazwę , jego `ConsoleApplication1`elementy programowania należą do obszaru nazw . Jeśli `Namespace Magnetosphere`zadeklarujesz, `Magnetosphere` odwołania do `ConsoleApplication1.Magnetosphere`projektu będą uzyskiwać dostęp .  
  
 Poniższe przykłady `Global` używają słowa kluczowego do deklarowania obszaru nazw poza głównym obszarem nazw dla projektu.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 W deklaracji obszaru `Global` nazw nie można zagnieżdżać w innej przestrzeni nazw.  
  
 Za pomocą [strony aplikacji, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) można wyświetlić i zmodyfikować **główny obszar nazw** projektu.  W przypadku nowych projektów **główny obszar nazw** domyślnie nazywa się nazwą projektu. Aby `Global` spowodować, że obszar nazw najwyższego poziomu, można wyczyścić wpis **głównego obszaru nazw,** tak aby pole było puste. Wyczyszczenie **głównego obszaru** nazw `Global` eliminuje potrzebę słowa kluczowego w deklaracjach obszaru nazw.  
  
 Jeśli `Namespace` instrukcja deklaruje nazwę, która jest również obszar nazw w .NET Framework, .NET Framework obszar nazw staje się niedostępny, jeśli `Global` słowo kluczowe nie jest używany w pełni kwalifikowana nazwa. Aby włączyć dostęp do tego obszaru nazw `Global` programu .NET `Global` Framework bez `Namespace` użycia słowa kluczowego, można dołączyć słowo kluczowe w instrukcji.  
  
 Poniższy przykład `Global` ma słowo `System.Text` kluczowe w deklaracji obszaru nazw.  
  
 Jeśli `Global` słowo kluczowe nie było obecne <xref:System.Text.StringBuilder> w deklaracji obszaru nazw, `Global.System.Text.StringBuilder`nie można uzyskać dostępu bez określenia . W przypadku `ConsoleApplication1`projektu o `System.Text` nazwie `ConsoleApplication1.System.Text` odwołania `Global` będą miały dostęp, jeśli słowo kluczowe nie zostało użyte.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Referencje i instrukcja Imports](references-and-the-imports-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Pisanie kodu dla rozwiązań pakietu Office](/visualstudio/vsto/writing-code-in-office-solutions)
