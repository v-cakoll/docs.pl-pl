---
title: Struktura programu Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: daaafa4877e9fc5abd7e720c5a91aa61f24a686c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686052"
---
# <a name="structure-of-a-visual-basic-program"></a>Struktura programu Visual Basic
Program Visual Basic jest tworzone na podstawie standardowych bloków konstrukcyjnych. A *rozwiązania* składa się z co najmniej jeden projekt. A *projektu* z kolei może zawierać jeden lub więcej zestawów. Każdy *zestawu* jest kompilowany przy użyciu jednego lub więcej plików źródłowych. A *plik źródłowy* zawiera definicję i implementację klasy, struktury, moduły i interfejsy, które ostatecznie zawierają całego kodu.  
  
 Aby uzyskać więcej informacji o tych bloków konstrukcyjnych programu w języku Visual Basic, zobacz [rozwiązania i projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio) i [zestawy i Globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Elementy programowania poziomie plików  
 Po uruchomieniu projektu lub pliku i otworzyć Edytor kodu, zobaczysz kodu już, jak i w odpowiedniej kolejności. Wszelki kod, który napiszesz należy wykonać następującą sekwencję:  
  
1.  `Option` Instrukcje  
  
2.  `Imports` Instrukcje  
  
3.  `Namespace` instrukcje i poziomie przestrzeni nazw elementów  
  
 Jeśli wprowadzasz instrukcji w innej kolejności, może spowodować błędy kompilacji.  
  
 Program może również zawierać instrukcjach kompilacji warunkowej. Możesz rozdzielać rzędy je w pliku źródłowym między instrukcje poprzedniego sekwencji.  
  
### <a name="option-statements"></a>Opcja instrukcji  
 `Option` instrukcje ustanowić podstawowe zasady kolejnych kodu, co pomaga zapobiec użyciu błędów składniowych i logicznych. [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md) gwarantuje, że wszystkie zmienne są deklarowane i poprawna, która skraca czas debugowania. [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md) pomaga zminimalizować logiki błędów i utraty danych, może wystąpić, gdy pracujesz między zmiennych o różnych typach danych. [Instrukcji porównanie opcji](../../../visual-basic/language-reference/statements/option-compare-statement.md) określa sposób ciągi są porównywane ze sobą, na podstawie ich `Binary` lub `Text` wartości.  
  
### <a name="imports-statements"></a>Instrukcji Imports  
 Możesz uwzględnić [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do zaimportowania nazwy zdefiniowane poza projektem. `Imports` Instrukcji umożliwia kodu do odwoływania się do klas i innych typów zdefiniowanych w importowanych przestrzeni nazw, bez konieczności ich kwalifikowania. Można użyć tylu `Imports` instrukcji zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [odwołania i Importy — instrukcja](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Instrukcje Namespace  
 Przestrzenie nazw pomocy, organizowanie i klasyfikowanie w celu ułatwienia grupowanie i uzyskiwania dostępu do elementów programowania. Możesz użyć [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md) do klasyfikowania następujące instrukcje w ramach danego obszaru nazw. Aby uzyskać więcej informacji, zobacz [przestrzeni nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Instrukcje kompilacji warunkowej  
 Instrukcje kompilacji warunkowej może znajdować się w praktycznie dowolnym miejscu w pliku źródłowym. Powodują one fragmenty kodu może być dołączone lub wykluczone w czasie kompilacji w zależności od określonych kryteriów. Umożliwia także je do debugowania aplikacji, ponieważ kod warunkowy działa tylko w trybie debugowania. Aby uzyskać więcej informacji, zobacz [kompilacji warunkowej](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Poziom Namespace elementy programowania  
 Klasy, struktury i moduły zawiera cały kod w pliku źródłowym. Są one *poziomie przestrzeni nazw* elementy, które może się pojawić w przestrzeni nazw lub na poziomie pliku źródłowego. Przechowują deklaracje wszystkie inne elementy programowania. Interfejsy, które zdefiniować element podpisów, ale nie implementacji, są również wyświetlane na poziomie modułu. Aby uzyskać więcej informacji na poziomie modułu elementów zobacz następujące tematy:  
  
-   [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Elementy danych na poziomie przestrzeni nazw są, wyliczenia i delegaty.  
  
## <a name="module-level-programming-elements"></a>Poziom modułu elementy programowania  
 Procedury operatorów, właściwości i zdarzenia są tylko elementy programowania, które mogą zawierać kod wykonywalny (instrukcji, które wykonują akcje w czasie wykonywania). Są one *poziom modułu* elementach programu. Aby uzyskać więcej informacji na temat elementów poziom procedury zobacz następujące tematy:  
  
-   [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Elementy danych na poziomie modułu są zmienne, stałe, wyliczenia i delegaty.  
  
## <a name="procedure-level-programming-elements"></a>Poziom procedury elementy programowania  
 Większość zawartości *poziom procedury* elementy są instrukcje wykonywalne, które stanowią kodu w czasie wykonywania programu. Cały kod wykonywalny musi znajdować się w niektórych procedury (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Aby uzyskać więcej informacji, zobacz [instrukcji](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Elementy danych na poziomie procedury są ograniczone do stałe i zmienne lokalne.  
  
## <a name="the-main-procedure"></a>Główne procedury  
 `Main` Procedura jest pierwszy kod do uruchomienia po załadowaniu aplikacji. `Main` Służy jako początkowy punkt i ogólna kontrola dla danej aplikacji. Istnieją cztery różne typy `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Najbardziej typowe odmiana tej procedury jest `Sub Main()`. Aby uzyskać więcej informacji, zobacz [procedura Main w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Zobacz także
- [Procedura główna w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
- [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Ograniczenia Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)
