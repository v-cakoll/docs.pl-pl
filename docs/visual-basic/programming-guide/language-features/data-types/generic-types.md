---
title: Typy ogólne w Visual Basic (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: 3a419fb38d3b97b08c8aaa094265d8b426429ae4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082750"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Typy ogólne w Visual Basic (Visual Basic)
A *typu ogólnego* jest pojedynczego elementu programistycznego, która dostosowuje się do wykonywania funkcji dla różnych typów danych. Po zdefiniowaniu klasy ogólnej lub procedura ma definiuje oddzielnych wersji dla każdego typu danych, dla którego możesz chcieć wykonać tę funkcję.  
  
 Analogii jest śrubokręta zestawu przy użyciu głowic wymiennych. Zbadaj gwintowanym, należy włączyć, a następnie wybierz poprawny nagłówek dla tego gwintowanym (prosty, progów, oznaczone). Gdy wstawiasz head prawidłowe dojście śrubokręt, wykonujesz dokładnie tej samej funkcji z śrubokręt, a mianowicie włączenie śrubę.  
  
 ![Diagram przedstawiający śrubokręt ustawiony jako ogólnego narzędzia](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
Ustaw jako ogólnego narzędzia śrubokręt  
  
 Podczas definiowania typu ogólnego parametryzuj z co najmniej jeden typ danych. Dzięki temu używając kodu, aby dostosować typy danych do swoich wymagań. Kod można zadeklarować kilka różnych elementów programowania, od ogólnego elementu każdej z nich na inny zestaw typów danych. Jednak wszystkie elementy zadeklarowane wykonać identyczne, niezależnie od tego, jakiego typu dane, które używają.  
  
 Na przykład możesz chcieć tworzenie i używanie klasy kolejki, która działa na określony typ danych, takich jak `String`. Można zadeklarować klasy z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 Teraz możesz używać `stringQ` wyłącznie w `String` wartości. Ponieważ `stringQ` dla konkretnego `String` zamiast trwa lotniczych `Object` wartości, nie masz późne powiązania lub typ konwersji. To pozwala zaoszczędzić czas wykonywania i zmniejsza błędy czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat korzystania z typu ogólnego, zobacz [porady: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Przykład klasy ogólnej  
 Poniższy przykład pokazuje szkielet definicją klasy ogólnej.  
  
 [!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 W poprzednim szkielet `t` jest *parametr typu*, oznacza to, symbol zastępczy dla typu danych, które podasz, kiedy Deklarujesz klasę. Gdzie indziej w kodzie, można zadeklarować różne wersje `classHolder` podając różne typy danych dla `t`. Poniższy przykład przedstawia dwa oświadczenia.  
  
 [!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 Poprzedni instrukcje deklarują *skonstruowany klasy*, w którym określonego typu zastępuje parametr typu. Ta zastępowania są propagowane w całym kodzie w obrębie klasy skonstruowany. Poniższy przykład pokazuje, jakie `processNewItem` procedura wygląda podobnie jak w `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [porady: Definiowanie klasy, może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Kwalifikujące się elementy programowania  
 Można zdefiniować i użyj klasy ogólne, struktury, interfejsy, procedury i delegatów. Należy pamiętać, że [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definiuje kilka klas ogólnych, struktur i interfejsów, które reprezentują elementy rodzajowe często używane. <xref:System.Collections.Generic?displayProperty=nameWithType> Przestrzeń nazw zawiera słowników, list, kolejek i stosów. Przed zdefiniowaniem własne ogólnego elementu, należy sprawdzić, czy jest już dostępna w <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Procedury nie są typami, ale można zdefiniować i użyć procedury ogólne. Zobacz [procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Zalety typów ogólnych  
 Typ ogólny służy jako podstawa do deklarowania wiele różnych elementów programowania, każde z nich działa na określony typ danych. Alternatywy dla typu ogólnego są:  
  
1.  Korzysta z jednego typu `Object` typu danych.  
  
2.  Zbiór *specyficznych dla typu* wersji typu, każda wersja indywidualnie zakodowanych i działających na jeden określony typ danych, takich jak `String`, `Integer`, lub typ zdefiniowany przez użytkownika, takie jak `customer`.  
  
 Ogólny typ ma następujące korzyści za pośrednictwem następujących alternatyw:  
  
-   **Bezpieczeństwo typów.** Typy ogólne wymusić, kontrola typów w czasie kompilacji. Na podstawie typów `Object` akceptować dowolny typ danych, a następnie należy napisać kod, aby sprawdzić, czy typ danych wejściowych jest dopuszczalna. Za pomocą typów ogólnych kompilator może przechwycić niezgodności typu przed w czasie wykonywania.  
  
-   **Wydajność.** Typy ogólne nie jest konieczne *pole* i *unbox* danych, ponieważ każdy z nich jest przeznaczone do jednego typu danych. Operacje na podstawie `Object` musi polu typów danych wejściowych w celu przekonwertowania ich do `Object` i rozpakowywanie danych przeznaczone dla danych wyjściowych. Opakowywanie i rozpakowywanie obniżenie wydajności.  
  
     Na podstawie typów `Object` są również z późnym wiązaniem, co oznacza, że uzyskanie dostępu do swoich elementów członkowskich wymaga dodatkowego kodu w czasie wykonywania. Zmniejsza to wydajności.  
  
-   **Konsolidacja kodu.** Kod w typie ogólnym musi być zdefiniowany tylko jeden raz. Zbiór specyficznych dla typu wersji typu muszą być replikowane ten sam kod w każdej wersji, jedyną różnicą jest typ danych specyficznych dla danej wersji. Za pomocą typów ogólnych wersji typu są wszystkie generowane na podstawie oryginalnego typu ogólnego.  
  
-   **Możesz pisać kod ponownego użycia.** Kod, który nie zależy od określonego typu danych mogą być używane różne typy danych, jeśli jest ona typu ogólnego. Nawet w przypadku typu danych, który nie pierwotnie przewidzieć często może używać go.  
  
-   **Obsługa środowiska IDE.** Gdy używasz skonstruowanego typu zadeklarowane z typem ogólnym, zintegrowanego środowiska programistycznego (IDE) daje więcej obsługę podczas opracowywania kodu. Na przykład technologia IntelliSense można wyświetlić opcje specyficzne dla typu argumentu konstruktora lub metody.  
  
-   **Algorytmy rodzajowe.** Abstrakcyjna algorytmy, które są niezależne od typu dobrze nadają się do typów ogólnych. Na przykład ogólny procedury, która sortuje elementy przy użyciu <xref:System.IComparable> interfejsu może być używany z dowolnego typu danych, który implementuje <xref:System.IComparable>.  
  
## <a name="constraints"></a>Ograniczenia  
 Mimo że kod w definicji typu ogólnego należy jako typ niezależne od jak to możliwe, może być konieczne wymagają możliwości dowolnego typu danych dostarczane do danego typu ogólnego. Na przykład, jeśli chcesz porównać dwa elementy na potrzeby sortowania i sortowania, typem danych, musi implementować <xref:System.IComparable> interfejsu. To wymaganie można wymusić, dodając *ograniczenie* na parametr typu.  
  
### <a name="example-of-a-constraint"></a>Przykład ograniczenie  
 W poniższym przykładzie pokazano szkielet definicję klasy z ograniczeniem, która wymaga argumentu typu do zaimplementowania <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 Jeśli kolejne kod próbuje utworzyć klasę z `itemManager` dostarczenie typ, który nie implementuje <xref:System.IComparable>, kompilator sygnalizuje błąd.  
  
### <a name="types-of-constraints"></a>Typy ograniczeń  
 Ograniczenia usługi można określić następujące wymagania w dowolnej kombinacji:  
  
-   Argument typu musi implementować jeden lub więcej interfejsów  
  
-   Argument typu musi być typu, lub dziedziczyć z co najwyżej jednej klasy  
  
-   Argument typu musi ujawniać konstruktor bez parametrów dostępny do kodu, który tworzy obiekty od niego  
  
-   Argument typu musi być *odwołania do typu*, lub musi być *typ wartości*  
  
 Jeśli zachodzi potrzeba narzucane przez więcej niż jedno wymaganie, możesz użyć rozdzielonych przecinkami *lista ograniczeń* w nawiasach klamrowych (`{ }`). Aby wymagać dostępny konstruktor, obejmują [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe na liście. Aby wymagać typem referencyjnym, obejmują `Class` słowa kluczowego; wymaga typu wartości dołączysz `Structure` — słowo kluczowe.  
  
 Aby uzyskać więcej informacji na temat ograniczeń, zobacz [lista typów](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Przykład wielu ograniczeń  
 Poniższy przykład pokazuje szkielet definicji klasy ogólnej z listą ograniczeń dla parametru typu. W kodzie, który tworzy wystąpienie tej klasy, argument typu musi implementować zarówno <xref:System.IComparable> i <xref:System.IDisposable> interfejsy, jako typów referencyjnych i udostępnić dostępny konstruktora bez parametrów.  
  
 [!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a>Ważne terminy  
 Typy ogólne wprowadzenie i są używane następujące pojęcia:  
  
-   *Typ ogólny*. Definicja klasy, struktury, interfejsu, procedura lub delegata, dla którego należy podać co najmniej jednego typu danych w przypadku deklarowania.  
  
-   *Parametr typu*. W definicji typu ogólnego symbol zastępczy dla typu danych podajesz podczas deklarowania typu.  
  
-   *Argument typu*. Typ konkretnych danych, który zastępuje parametr typu w deklaracji typu skonstruowany z typu ogólnego.  
  
-   *Ograniczenie*. Warunek dla parametru typu, który ogranicza możliwość użycia argumentów typu można podać dla niego. Ograniczenie może wymagać, że argument typu musi implementuje danego interfejsu, lub dziedziczyć z konkretną klasą, ma dostępne konstruktora bez parametrów lub być typem referencyjnym lub typem wartości. Można połączyć te ograniczenia, ale można określić co najwyżej jedną klasę.  
  
-   *Skonstruowany typ*. Klasy, struktury, interfejsu, procedura lub delegata zadeklarowane z typem ogólnym poprzez dostarczenie argumentów typu dla jego parametrów typu.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)  
- [z](../../../../visual-basic/language-reference/statements/of-clause.md)  
- [As](../../../../visual-basic/language-reference/statements/as-clause.md)  
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
- [Kowariancja i kontrawariancja](../../concepts/covariance-contravariance/index.md)  
- [Iteratory](../../../../visual-basic/programming-guide/concepts/iterators.md)
