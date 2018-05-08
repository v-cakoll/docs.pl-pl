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
ms.openlocfilehash: f86819f9bd3cbcceb4be696852655018868f4a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Typy ogólne w Visual Basic (Visual Basic)
A *typu ogólnego* jest pojedynczego elementu programistycznego, który dostosowuje się do wykonywania funkcji dla różnych typów danych. Podczas definiowania klasy ogólnej lub procedury, trzeba zdefiniować oddzielnych wersji dla każdego typu danych, dla których warto wykonywać te funkcje.  
  
 Odpowiednio jest śrubokręta ustawiony za pomocą głowic wymienne. Sprawdź śrubę należy włączyć i wybierz poprawny nagłówek dla tego gwintowanym (prosty, przekroczyła, starred). Po wstawisz head prawidłowe dojście śrubokręt, wykonana dokładnie tej samej funkcji śrubokręt, czyli wyłączenie śrubę.  
  
 ![Diagram przedstawiający śrubokręt ustawiony jako ogólnego narzędzia](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
Śrubokręt ustawiony jako narzędzie ogólne  
  
 Po zdefiniowaniu typu ogólnego parametryzacja z co najmniej jeden typ danych. Umożliwia to użycie kod, aby dostosować typy danych do swoich wymagań. Kod, mogą zadeklarować kilka różnych elementów programowania z ogólnego elementu każdej z nich na inny zestaw typów danych. Jednak wszystkie elementy zadeklarowane wykonywać identyczne, niezależnie od tego, jakie typy danych, które używają.  
  
 Na przykład możesz chcieć tworzenie i używanie klasy kolejki, która działa na typ danych, takich jak `String`. Można zadeklarować klasy z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, jak pokazano na poniższym przykładzie.  
  
 [!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 Można teraz używać `stringQ` wyłącznie w `String` wartości. Ponieważ `stringQ` jest specyficzna dla `String` zamiast trwa uogólniony dla `Object` wartości, nie dysponujesz późne wiązanie lub typ konwersji. To zaoszczędzić czas wykonywania i zmniejsza błędów czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat używania typu ogólnego, zobacz [porady: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Przykład klasy generycznej  
 Poniższy przykład przedstawia definicję szkielet ogólnej klasy.  
  
 [!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 W poprzednim szkielet `t` jest *parametr typu*, oznacza to symbol zastępczy dla typu danych, wprowadzona w deklaracji klasy. W innym miejscu w kodzie, mogą zadeklarować różnych wersjach `classHolder` podając różnych typów danych `t`. Poniższy przykład przedstawia dwa oświadczenia.  
  
 [!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 Powyższych instrukcji declare *skonstruowany klasy*, w którym określonego typu zastępuje parametru typu. To zastąpienie są propagowane w całym kodzie w klasie skonstruowane. W poniższym przykładzie pokazano, co `processNewItem` procedura wygląda podobnie jak w `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 Na przykład bardziej szczegółowy, zobacz [porady: Definiowanie klasy czy może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Kwalifikujące się elementy programowania  
 Można zdefiniować i użyj ogólny klasy, struktury, interfejsów, procedury i delegatów. Należy pamiętać, że [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definiuje kilka ogólnego klasy, struktury i interfejsy, które reprezentują często używanych elementów ogólnych. <xref:System.Collections.Generic?displayProperty=nameWithType> Przestrzeń nazw zawiera słowników, list, kolejek i stosy. Przed zdefiniowaniem własne ogólny element, należy sprawdzić, czy jest już dostępne w <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Procedury nie są typami, ale można zdefiniować i rodzajowy procedury. Zobacz [procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Zalety typów ogólnych  
 Typu ogólnego służy jako podstawa deklarowania kilka różnych elementów programowania, z których każdy działa na typ danych. Alternatywy dla typu ogólnego są:  
  
1.  Korzysta z jednego typu `Object` — typ danych.  
  
2.  Zestaw *określonego typu* wersje typu każdej wersji indywidualnie kodowany i działających na jednego określonego typu danych, takich jak `String`, `Integer`, lub typem zdefiniowane przez użytkownika, takie jak `customer`.  
  
 Typu ogólnego ma następujące zalety za pośrednictwem następujących alternatyw:  
  
-   **Zabezpieczenie typów.** Typy ogólne Wymuś sprawdzanie typów w czasie kompilacji. Na podstawie typów `Object` Zaakceptuj dowolny typ danych, a następnie należy napisać kod, aby sprawdzić, czy dopuszczalny jest typem danych wejściowych. Z typów ogólnych kompilator może przechwycić niezgodności typu przed w czasie wykonywania.  
  
-   **Wydajność.** Typy ogólne nie ma potrzeby *pole* i *unbox —* danych, ponieważ każdy z nich jest przeznaczone do jednego typu danych. Operacje na podstawie `Object` musi polu typów danych wejściowych do przeprowadzenia tej konwersji do `Object` i unbox — danych przeznaczonych dla danych wyjściowych. Opakowywanie i rozpakowywanie obniżyć wydajność.  
  
     Na podstawie typów `Object` są również późnym wiązaniem, co oznacza, że dostęp do ich elementy Członkowskie wymaga dodatkowego kodu w czasie wykonywania. Zmniejsza to także wydajności.  
  
-   **Konsolidacja kodu.** Kod w typie ogólnym musi być zdefiniowany tylko raz. Zestaw wersji określonego typu typu musi zostać zreplikowana ten sam kod w każdej wersji, a jedyną różnicą jest typu danych określonego dla tej wersji. Z typów ogólnych wersji określonego typu są wszystkie generowane z oryginalnego typu ogólnego.  
  
-   **Kod ponownego użycia.** Kod, który nie zależy od typu danych mogą być ponownie używane przy użyciu różnych typów danych, jeśli jest ona typu ogólnego. Nawet w przypadku typu danych, który nie pierwotnie prognozowania często może używać go.  
  
-   **Obsługa środowiska IDE.** Użycie skonstruowanego typu zadeklarowane z typem ogólnym, zintegrowane środowisko programistyczne (IDE) może zapewnić więcej pomocy technicznej podczas tworzenia kodu. Na przykład IntelliSense mogą być prezentowane opcje określonego typu jako argumentu do konstruktora lub metody.  
  
-   **Algorytmy ogólnego.** Abstrakcyjna algorytmy, które są niezależne od typu nadaje się do typów ogólnych. Na przykład ogólny procedury sortujące elementów przy użyciu <xref:System.IComparable> interfejsu może być używany z dowolnego typu danych, który implementuje <xref:System.IComparable>.  
  
## <a name="constraints"></a>Ograniczenia  
 Chociaż kod w definicji typu ogólnego powinien być jako typ niezależny jak to możliwe, konieczne może być wymagają możliwości dowolny typ danych dostarczony do typu ogólnego. Na przykład, jeśli chcesz porównać dwóch elementów na potrzeby sortowania lub sortowania, typem danych musi implementować <xref:System.IComparable> interfejsu. To wymaganie można wymusić przez dodanie *ograniczenia* do parametru typu.  
  
### <a name="example-of-a-constraint"></a>Przykład ograniczenia  
 W poniższym przykładzie przedstawiono szkielet definicję klasy z ograniczeniem wymaga argumentu typu, aby zaimplementować <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 Jeśli kod kolejnych prób utworzenia klasy z `itemManager` dostarczanie typu, który nie implementuje <xref:System.IComparable>, kompilator sygnały wystąpił błąd.  
  
### <a name="types-of-constraints"></a>Typy ograniczeń  
 W dowolnej kombinacji z ograniczeniem można określić następujące wymagania:  
  
-   Argument typu musi implementować jeden lub więcej interfejsów  
  
-   Argument typu musi być typu lub dziedziczyć co najwyżej jedną klasę  
  
-   Argument typu musi ujawniać konstruktor bez parametrów dostępnych do kodu, który tworzy obiekty od niego  
  
-   Typ argumentu musi być *zawierają odwołania do typu*, lub musi być *typu wartości*  
  
 Jeśli musisz skonfigurować więcej niż jedno wymaganie, możesz użyć rozdzielone przecinkami *listy ograniczenie* w nawiasach klamrowych (`{ }`). Aby wymagać dostępny konstruktor, obejmują [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe na liście. Aby wymagać typu odwołania, obejmują `Class` słowa kluczowego; wymaga typu wartości wprowadzeniem `Structure` — słowo kluczowe.  
  
 Aby uzyskać więcej informacji dotyczących ograniczeń, zobacz [lista typów](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Przykład wielu ograniczeń  
 Poniższy przykład przedstawia szkielet definicji klasy ogólnej z listą ograniczenia dla parametru typu. W kodzie, który tworzy wystąpienie tej klasy, argument Typ musi implementować zarówno <xref:System.IComparable> i <xref:System.IDisposable> interfejsy, być typem referencyjnym i ujawnia dostępny konstruktor bez parametrów.  
  
 [!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a>Ważne pojęcia  
 Typy ogólne wprowadzić i używane następujące pojęcia:  
  
-   *Typ ogólny*. Definicja klasy, struktury, interfejsu, procedura lub delegata, dla której należy podać co najmniej jednego typu danych podczas Zadeklaruj ją.  
  
-   *Parametr typu*. W definicji typu ogólnego symbolem zastępczym dla typu danych podanych w deklaracji typu.  
  
-   *Argument typu*. Typ określonych danych, który zastępuje parametr typu w deklaracji skonstruowanego typu z typu ogólnego.  
  
-   *Ograniczenie*. Warunek na parametr typu, który ogranicza argument typu można podać dla niego. Ograniczenie może wymagać argument typu musi wykonania konkretnego interfejsu, można lub dziedziczyć po określonej klasy, ma dostępny konstruktora bez parametrów lub być typem referencyjnym lub typem wartości. Można połączyć tych warunków ograniczających, ale można określić co najwyżej jedną klasę.  
  
-   *Tworzony typ*. Klasy, struktury, interfejsu, procedura lub delegata zadeklarowane z typem ogólnym, podając argumentów typu dla swoich parametrów typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [z](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [As](../../../../visual-basic/language-reference/statements/as-clause.md)  
 [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Kowariancja i kontrawariancja](../../concepts/covariance-contravariance/index.md)  
 [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
