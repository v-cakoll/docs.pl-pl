---
title: Typy ogólne
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
ms.openlocfilehash: b14c7a3f1f667e7c13ec0ae46185ed3ece92beb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394055"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Typy ogólne w Visual Basic (Visual Basic)
*Typ ogólny* to pojedynczy element programistyczny, który dostosowuje się do wykonywania tych samych funkcji dla różnych typów danych. Podczas definiowania ogólnej klasy lub procedury nie trzeba definiować oddzielnej wersji dla każdego typu danych, dla którego można wykonać tę funkcję.  
  
 Analogowa jest śrubokrętem ustawionym z wymiennymi głowicami. Należy sprawdzić, czy jest włączony, i wybrać odpowiednią pozycję dla tego gwintu (prosty, przekreślony, oznaczona gwiazdkami). Po wstawieniu poprawnej głowy w uchwycie śrubokrętu należy wykonać dokładną funkcję ze śrubokrętem, a mianowicie przekształceniem.  
  
 ![Diagram zestawu śrubokrętów z różnymi nagłówkami.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Podczas definiowania typu ogólnego należy Sparametryzuj go z co najmniej jednym typem danych. Pozwala to na użycie kodu do dopasowania typów danych do swoich wymagań. Kod może zadeklarować kilka różnych elementów programistycznych z elementu ogólnego, każdy z nich działa na innym zestawie typów danych. Jednak zadeklarowane elementy wszystkie wykonują identyczną logikę, niezależnie od tego, jakie typy danych są używane.  
  
 Na przykład możesz chcieć utworzyć i użyć klasy kolejki, która działa na określonym typie danych, takim jak `String` . Można zadeklarować takie klasy z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> , jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Można teraz używać `stringQ` do pracy wyłącznie z `String` wartościami. Ponieważ `stringQ` jest specyficzny dla `String` , a nie uogólniony dla `Object` wartości, nie masz późnych powiązań ani konwersji typu. Pozwala to zaoszczędzić czas wykonywania i skraca błędy czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat korzystania z typu ogólnego, zobacz [How to: use generyczn Class](how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Przykład klasy generycznej  
 Poniższy przykład przedstawia definicję szkieletu klasy generycznej.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 W poprzednim szkieletzie `t` jest *parametrem typu*, który jest symbolem zastępczym dla typu danych dostarczanym podczas deklarowania klasy. W innym miejscu kodu można zadeklarować różne wersje programu, `classHolder` dostarczając różne typy danych dla `t` . Poniższy przykład pokazuje dwie takie deklaracje.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 Powyższe instrukcje deklarują *skonstruowane klasy*, w których określony typ zastępuje parametr typu. Ten zamiennik jest propagowany w całym kodzie w ramach konstruowanej klasy. Poniższy przykład pokazuje, `processNewItem` jak wygląda ta procedura `integerClass` .  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, zobacz [jak: Definiowanie klasy, która może zapewnić identyczną funkcjonalność dla różnych typów danych](how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Kwalifikujące się elementy programistyczne  
 Można definiować i używać klas ogólnych, struktur, interfejsów, procedur i delegatów. Należy zauważyć, że .NET Framework definiuje kilka klas ogólnych, struktur i interfejsów, które reprezentują często używane elementy ogólne. <xref:System.Collections.Generic?displayProperty=nameWithType>Przestrzeń nazw zawiera słowniki, listy, kolejki i stosy. Przed zdefiniowaniem własnego elementu generycznego, sprawdź, czy jest on już dostępny w programie <xref:System.Collections.Generic?displayProperty=nameWithType> .  
  
 Procedury nie są typami, ale można definiować i używać procedur ogólnych. Zapoznaj [się z procedurami ogólnymi w Visual Basic](generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Zalety typów ogólnych  
 Typ ogólny służy jako podstawa do deklarowania kilku różnych elementów programistycznych, z których każdy działa na określonym typie danych. Alternatywy dla typu ogólnego są:  
  
1. Pojedynczy typ, który działa na `Object` typie danych.  
  
2. Zestaw wersji typu *specyficznego dla typu* , każdej wersji osobno zakodowanej i działającej na jednym określonym typie danych, na przykład `String` , `Integer` lub typu zdefiniowanego przez użytkownika, takiego jak `customer` .  
  
 Typ ogólny ma następujące zalety w porównaniu z tymi alternatywami:  
  
- **Bezpieczeństwo typu.** Typy ogólne wymuszają sprawdzanie typu w czasie kompilacji. Typy na podstawie `Object` akceptowania dowolnego typu danych i należy napisać kod, aby sprawdzić, czy typ danych wejściowych jest akceptowalny. W przypadku typów ogólnych kompilator może przechwytywać niezgodności typów przed uruchomieniem.  
  
- **Skuteczności.** Typy ogólne nie mają *pola* i *Unbox* dane, ponieważ każdy z nich jest wyspecjalizowany dla jednego typu danych. Operacje oparte na `Object` typie danych wejściowej muszą mieć pole, aby przekonwertować je na `Object` i Unbox dane przeznaczone do danych wyjściowych. Wypakowywanie i rozpakowywanie zmniejszanie wydajności.  
  
     Typy oparte na programie `Object` są również opóźnione, co oznacza, że dostęp do swoich elementów członkowskich wymaga dodatkowego kodu w czasie wykonywania. Zmniejsza to również wydajność.  
  
- **Konsolidacja kodu.** Kod w typie ogólnym musi być zdefiniowany tylko raz. Zestaw wersji typu specyficznego dla typu musi replikować ten sam kod w każdej wersji, z jedyną różnicą charakterystyczną dla konkretnego typu danych dla tej wersji. W przypadku typów ogólnych wersje specyficzne dla typu są generowane na podstawie oryginalnego typu ogólnego.  
  
- **Ponowne użycie kodu.** Kod, który nie zależy od określonego typu danych, może być ponownie używany z różnymi typami danych, jeśli jest ogólny. Często można ponownie użyć tego elementu nawet z typem danych, który nie został pierwotnie przewidywalny.  
  
- **Obsługa środowiska IDE.** Jeśli używasz złożonego typu zadeklarowanego z typu ogólnego, zintegrowane środowisko programistyczne (IDE) może zapewnić lepszą obsługę podczas tworzenia kodu. Na przykład technologia IntelliSense może wyświetlić opcje specyficzne dla danego typu dla argumentu w konstruktorze lub metodzie.  
  
- **Algorytmy ogólne.** Abstrakcyjne algorytmy, które są niezależne od typu, są dobrymi kandydatami dla typów ogólnych. Na przykład ogólna procedura, która sortuje elementy przy użyciu <xref:System.IComparable> interfejsu, może być używana z dowolnym typem danych, który implementuje <xref:System.IComparable> .  
  
## <a name="constraints"></a>Ograniczenia  
 Chociaż kod w definicji typu ogólnego powinien być niezależny od typu, konieczne może być wymaganie pewnej możliwości dowolnego typu danych dostarczonego do typu ogólnego. Na przykład jeśli chcesz porównać dwa elementy na potrzeby sortowania lub sortowania, ich typ danych musi implementować <xref:System.IComparable> interfejs. To wymaganie można wymusić, dodając *ograniczenie* do parametru typu.  
  
### <a name="example-of-a-constraint"></a>Przykład ograniczenia  
 Poniższy przykład przedstawia definicję szkieletu klasy z ograniczeniami wymagającymi argumentu typu do zaimplementowania <xref:System.IComparable> .  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Jeśli kolejny kod próbuje utworzyć klasę z `itemManager` dostarczania typu, który nie implementuje <xref:System.IComparable> , kompilator sygnalizuje błąd.  
  
### <a name="types-of-constraints"></a>Typy ograniczeń  
 Ograniczenie może określać następujące wymagania w dowolnej kombinacji:  
  
- Argument typu musi implementować jeden lub więcej interfejsów  
  
- Argument typu musi być typu lub dziedziczyć po, co najwyżej jedną klasę  
  
- Argument typu musi ujawniać konstruktora bez parametrów dostępnego dla kodu, który tworzy obiekty z niego  
  
- Argument typu musi być *typem referencyjnym*lub musi być *typem wartości*  
  
 Jeśli konieczne jest nakładanie więcej niż jednego wymagania, należy użyć *listy ograniczeń* rozdzielanych przecinkami ( `{ }` ). Aby wymagać konstruktora dostępnego, na liście należy umieścić słowo kluczowe [New Operator](../../../language-reference/operators/new-operator.md) . Aby wymagać typu referencyjnego, należy dołączyć `Class` słowo kluczowe; aby wymagać typu wartości, należy dołączyć `Structure` słowo kluczowe.  
  
 Aby uzyskać więcej informacji o ograniczeniach, zobacz [Type list](../../../language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Przykład wielu ograniczeń  
 Poniższy przykład przedstawia definicję szkieletu klasy generycznej z listą ograniczeń w parametrze typu. W kodzie, który tworzy wystąpienie tej klasy, argument typu musi implementować zarówno <xref:System.IComparable> interfejsy, jak i <xref:System.IDisposable> , być typem referencyjnym i uwidaczniać dostępny Konstruktor bez parametrów.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Ważne warunki  
 Typy ogólne wprowadzają i korzystają z następujących warunków:  
  
- *Typ ogólny*. Definicja klasy, struktury, interfejsu, procedury lub delegata, dla którego podczas deklarowania należy podać co najmniej jeden typ danych.  
  
- *Parametr typu*. W definicji typu ogólnego, symbol zastępczy dla typu danych dostarczanego podczas deklarowania typu.  
  
- *Typ argumentu*. Określony typ danych, który zastępuje parametr typu w przypadku deklarowania konstruowanego typu z typu ogólnego.  
  
- *Ograniczenie*. Warunek w parametrze typu, który ogranicza typ argumentu, który można dla niego podać. Ograniczenie może wymagać, aby argument typu musi implementować określony interfejs, być lub dziedziczyć z określonej klasy, mieć dostępny Konstruktor bez parametrów lub być typem referencyjnym lub typem wartości. Można połączyć te ograniczenia, ale można określić co najwyżej jedną klasę.  
  
- *Typ skonstruowany*. Klasa, struktura, interfejs, procedura lub delegat zadeklarowany z typu ogólnego przez dostarczenie argumentów typu dla parametrów typu.  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Znaki typu](type-characters.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Konwersje plików w Visual Basic](type-conversions.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Typy danych](../../../language-reference/data-types/index.md)
- [Z](../../../language-reference/statements/of-clause.md)
- [Definicj](../../../language-reference/statements/as-clause.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
- [Kowariancja i kontrawariancja](../../concepts/covariance-contravariance/index.md)
- [Iteratory](../../concepts/iterators.md)
