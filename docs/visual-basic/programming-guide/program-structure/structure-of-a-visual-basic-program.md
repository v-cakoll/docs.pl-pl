---
title: Struktura programu Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5c45cc8982a03d5bdd974434164187b03529ae05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654833"
---
# <a name="structure-of-a-visual-basic-program"></a>Struktura programu Visual Basic
Program Visual Basic jest tworzone na podstawie standardowych bloków konstrukcyjnych. A *rozwiązania* składa się z co najmniej jeden projekt. A *projektu* z kolei może zawierać jeden lub więcej zestawów. Każdy *zestawu* ma być kompilowana przy użyciu jednego lub więcej plików źródłowych. A *plik źródłowy* zawiera definicję, jak i implementację klasy, struktury, moduły i interfejsów, które ponoszą ostateczną zawierające cały kod.  
  
 Aby uzyskać więcej informacji o tych bloków konstrukcyjnych programu Visual Basic, zobacz [rozwiązań i projektów](/visualstudio/ide/solutions-and-projects-in-visual-studio) i [zestawy i Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Elementy programowania poziomu plików  
 Po uruchomieniu pliku lub projektu i Otwórz Edytor kodu, zostanie wyświetlony niektórych kod już na miejscu i w odpowiedniej kolejności. Kod napisany należy wykonać następującej kolejności:  
  
1.  `Option` Instrukcje  
  
2.  `Imports` Instrukcje  
  
3.  `Namespace` instrukcje i elementów na poziomie przestrzeni nazw  
  
 Jeśli wprowadzisz instrukcje w innej kolejności, może spowodować błędy kompilacji.  
  
 Program może również zawierać instrukcji kompilacji warunkowej. Można intersperse je w pliku źródłowym między instrukcje poprzedniego sekwencji.  
  
### <a name="option-statements"></a>Opcja — instrukcje  
 `Option` instrukcje ustanowić podstawowe zasady kolejnych kodu, pomaga uniknąć błędów składni i logiki. [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md) gwarantuje, że wszystkie zmienne są zadeklarowane i wpisana poprawnie, co zmniejsza czas debugowania. [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md) pozwala zminimalizować logiki błędów i utraty danych, które mogą wystąpić podczas pracy między zmienne różnych typów danych. [Instrukcji porównanie opcji](../../../visual-basic/language-reference/statements/option-compare-statement.md) określa sposób ciągi są porównywane ze sobą, na podstawie ich `Binary` lub `Text` wartości.  
  
### <a name="imports-statements"></a>Imports — instrukcje  
 Można uwzględnić [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do zaimportowania nazwy zdefiniowane poza projektem. `Imports` Instrukcji umożliwia kodu do odwoływania się do klasy i innych typów zdefiniowanych w importowanych przestrzeni nazw, bez konieczności ich kwalifikacji. Można użyć jako wiele `Imports` instrukcje zależnie od potrzeb. Aby uzyskać więcej informacji, zobacz [referencje i Importy — instrukcja](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Namespace — instrukcje  
 Przestrzenie nazw pomocy organizowanie i ich klasyfikację w celu ułatwienia grupowanie i uzyskiwania dostępu do elementów programowania. Możesz użyć [instrukcji Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) do klasyfikowania następujące instrukcje w określonej przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [przestrzeni nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Kompilacja warunkowa — instrukcje  
 Kompilacja warunkowa instrukcje może występować w niemal z dowolnego miejsca w pliku źródłowego. Spowodują one części kodu mają być uwzględnione lub wykluczone w czasie kompilacji, w zależności od określonych warunków. Umożliwia także je do debugowania aplikacji, ponieważ kod warunkowego jest uruchamiany w tylko tryb debugowania. Aby uzyskać więcej informacji, zobacz [kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Namespace elementów programowania  
 Klasy, struktury i moduły zawierają cały kod w pliku źródłowym. Są one *poziomie przestrzeni nazw* elementów, które mogą być wyświetlane w przestrzeni nazw lub na poziomie pliku źródłowego. Posiadają deklaracje inne elementy programowania. Interfejsy, które zdefiniować element podpisów nie implementacji, są również wyświetlane na poziomie modułu. Aby uzyskać więcej informacji na poziomie modułu elementów zobacz następujące tematy:  
  
-   [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Elementy danych na poziomie przestrzeni nazw są wyliczenia i delegaty.  
  
## <a name="module-level-programming-elements"></a>Elementy programowania poziom modułu  
 Procedury operatorów, właściwości i zdarzenia są tylko elementy programowania, które mogą zawierać kod wykonywalny (instrukcji, które wykonują akcje w czasie wykonywania). Są one *poziom modułu* elementy programu. Aby uzyskać więcej informacji na temat elementów poziom procedury zobacz następujące tematy:  
  
-   [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Elementy danych na poziomie modułu są zmienne, stałe, wyliczenia i delegaty.  
  
## <a name="procedure-level-programming-elements"></a>Poziom procedury elementy programowania  
 Większość zawartości *poziom procedury* elementy są instrukcje wykonywalne, stanowiące kodu w czasie wykonywania programu. Cały kod wykonywalny musi być w niektórych procedury (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Aby uzyskać więcej informacji, zobacz [instrukcje](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Elementy danych na poziomie procedury są ograniczone do zmiennych lokalnych i stałe.  
  
## <a name="the-main-procedure"></a>Procedura główna  
 `Main` Procedura jest pierwszy kod uruchamiany, gdy został załadowany w aplikacji. `Main` Służy jako punkt początkowy i ogólnej kontroli aplikacji. Istnieją cztery odmian `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Najbardziej typowe różnych tej procedury jest `Sub Main()`. Aby uzyskać więcej informacji, zobacz [Main procedury w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedura główna w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Ograniczenia Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)
