---
title: Procedury
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: c0d9921704570c6984b203817aed8f5546b2f936
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408792"
---
# <a name="procedures-in-visual-basic"></a>Procedury w Visual Basic
*Procedura* jest blokiem instrukcji Visual Basic zawartych w instrukcji deklaracji ( `Function` ,,,, `Sub` `Operator` `Get` `Set` ) i zgodnej `End` deklaracji. Wszystkie instrukcje wykonywalne w Visual Basic muszą znajdować się w pewnej procedurze.  
  
## <a name="calling-a-procedure"></a>Wywoływanie procedury  
 Procedurę można wywołać z innego miejsca w kodzie. Jest to nazywane *wywołaniem procedury*. Gdy procedura zostanie zakończona, zwraca sterowanie do kodu, który został wywołany, który jest znany jako *kod wywołujący*. Kod wywołujący jest instrukcją lub wyrażeniem w instrukcji, która określa procedurę według nazwy i przenosi do niej kontrolkę.  
  
## <a name="returning-from-a-procedure"></a>Powrót z procedury  
 Procedura zwraca sterowanie do kodu wywołującego po zakończeniu jego działania. W tym celu można użyć [instrukcji return](../../../language-reference/statements/return-statement.md), odpowiedniej instrukcji [Exit instrukcji](../../../language-reference/statements/exit-statement.md) dla procedury lub instrukcji [End \<keyword> instrukcji](../../../language-reference/statements/end-keyword-statement.md) . Następnie formant przekazuje do kodu wywołującego po punkcie wywołania procedury.  
  
- Za pomocą `Return` instrukcji, kontrolka wraca bezpośrednio do kodu wywołującego. Instrukcje po `Return` instrukcji nie są uruchamiane. W tej samej procedurze można mieć więcej niż jedną `Return` instrukcję.  
  
- Za pomocą `Exit Sub` `Exit Function` instrukcji or, kontrola natychmiast wraca do kodu wywołującego. Instrukcje po `Exit` instrukcji nie są uruchamiane. Można mieć więcej niż jedną `Exit` instrukcję w tej samej procedurze i można mieszać `Return` i `Exit` wypełniać instrukcje w tej samej procedurze.  
  
- Jeśli procedura nie zawiera `Return` instrukcji lub `Exit` , zawiera `End Sub` `End Function` instrukcję or, `End Get` , lub, `End Set` po ostatniej instrukcji treści procedury. `End`Instrukcja zwraca bezpośrednio kontrolę do kodu wywołującego. W procedurze można mieć tylko jedną `End` instrukcję.  
  
## <a name="parameters-and-arguments"></a>Parametry i argumenty  
 W większości przypadków procedura musi działać na różnych danych przy każdym wywołaniu. Te informacje można przekazać do procedury w ramach wywołania procedury. Procedura definiuje zero lub więcej *parametrów*, z których każdy reprezentuje wartość, która oczekuje na przekazanie do niej. Odpowiadający każdemu parametrowi w definicji procedury jest *argumentem* w wywołaniu procedury. Argument reprezentuje wartość przekazana do odpowiadającego mu parametru w danym wywołaniu procedury.  
  
## <a name="types-of-procedures"></a>Typy procedur  
 Visual Basic używa kilku typów procedur:  
  
- [Procedury Sub](./sub-procedures.md) wykonują akcje, ale nie zwracają wartości do kodu wywołującego.  
  
- Procedury obsługi zdarzeń są `Sub` procedurami, które są wykonywane w odpowiedzi na zdarzenie wywoływane przez akcję użytkownika lub przez wystąpienie w programie.  
  
- [Procedury funkcyjne](./function-procedures.md) zwracają wartość do kodu wywołującego. Mogą wykonać inne akcje przed zwróceniem.

    Niektóre funkcje w języku C# zwracają *wartość zwracaną przez odwołanie*. Obiekty wywołujące funkcję mogą modyfikować wartość zwracaną, a ta modyfikacja jest odzwierciedlana w stanie wywoływanego obiektu. Począwszy od Visual Basic 2017, kod Visual Basic może korzystać z wartości zwracanych przez odwołanie, chociaż nie może zwracać wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania do zwracanych wartości](ref-return-values.md).
  
- [Procedury właściwości](./property-procedures.md) zwracają i przypisują wartości właściwości obiektów lub modułów.  
  
- [Procedury operatorów](./operator-procedures.md) definiują zachowanie operatora standardowego, gdy jeden lub oba operandy są nowo zdefiniowanymi klasami lub strukturą.  
  
- [Procedury ogólne w Visual Basic](../data-types/generic-procedures.md) definiują jeden lub więcej *parametrów typu* oprócz ich zwykłych parametrów, dzięki czemu kod wywołujący może przekazać określone typy danych przy każdym wywołaniu.  
  
## <a name="procedures-and-structured-code"></a>Procedury i Kod strukturalny  
 Każdy wiersz kodu wykonywalnego w aplikacji musi znajdować się wewnątrz procedury, takiej jak `Main` , `calculate` lub `Button1_Click` . Jeśli dzieli się duże procedury na mniejsze, aplikacja jest bardziej czytelna.  
  
 Procedury są przydatne do wykonywania powtarzających się lub udostępnionych zadań, takich jak często używane obliczenia, manipulowanie tekstem i formantami oraz operacje bazy danych. Można wywołać procedurę z wielu różnych miejsc w kodzie, aby można było używać procedur jako bloków konstrukcyjnych dla aplikacji.  
  
 Tworzenie struktury kodu przy użyciu procedur zapewnia następujące korzyści:  
  
- Procedury umożliwiają podział programów na osobne jednostki logiczne. Można debugować osobne jednostki w łatwiejszy sposób, niż można debugować cały program bez procedur.  
  
- Po opracowaniu procedur do użycia w jednym programie można używać ich w innych programach, często z małą lub bez modyfikacji. Dzięki temu można uniknąć duplikowania kodu.  
  
## <a name="see-also"></a>Zobacz też

- [Porady: tworzenie procedury](./how-to-create-a-procedure.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury własności](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Procedury ogólne w Visual Basic](../data-types/generic-procedures.md)
- [Obiekty i klasy](../objects-and-classes/index.md)
