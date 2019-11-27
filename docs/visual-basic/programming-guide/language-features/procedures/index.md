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
ms.openlocfilehash: b959f4b6986bc325c97c7cbe9aeee0341832f6cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345992"
---
# <a name="procedures-in-visual-basic"></a>Procedury w Visual Basic
*Procedura* jest blokiem instrukcji Visual Basic zawartych w instrukcji deklaracji (`Function`, `Sub`, `Operator`, `Get`, `Set`) i zgodnej deklaracji `End`. Wszystkie instrukcje wykonywalne w Visual Basic muszą znajdować się w pewnej procedurze.  
  
## <a name="calling-a-procedure"></a>Wywoływanie procedury  
 Procedurę można wywołać z innego miejsca w kodzie. Jest to nazywane *wywołaniem procedury*. Gdy procedura zostanie zakończona, zwraca sterowanie do kodu, który został wywołany, który jest znany jako *kod wywołujący*. Kod wywołujący jest instrukcją lub wyrażeniem w instrukcji, która określa procedurę według nazwy i przenosi do niej kontrolkę.  
  
## <a name="returning-from-a-procedure"></a>Powrót z procedury  
 Procedura zwraca sterowanie do kodu wywołującego po zakończeniu jego działania. W tym celu można użyć [instrukcji return](../../../../visual-basic/language-reference/statements/return-statement.md), odpowiedniej instrukcji [Exit instrukcji](../../../../visual-basic/language-reference/statements/exit-statement.md) dla procedury lub [\<końcowego słowa kluczowego procedury > instrukcji instrukcji](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) . Następnie formant przekazuje do kodu wywołującego po punkcie wywołania procedury.  
  
- Za pomocą instrukcji `Return`, kontrolka wraca bezpośrednio do kodu wywołującego. Instrukcje po instrukcji `Return` nie są uruchamiane. W tej samej procedurze można mieć więcej niż jedną instrukcję `Return`.  
  
- Za pomocą instrukcji `Exit Sub` lub `Exit Function`, kontrolka wraca bezpośrednio do kodu wywołującego. Instrukcje po instrukcji `Exit` nie są uruchamiane. W tej samej procedurze można mieć więcej niż jedną instrukcję `Exit` i można mieszać instrukcje `Return` i `Exit` w tej samej procedurze.  
  
- Jeśli procedura nie zawiera instrukcji `Return` ani `Exit`, zawiera instrukcję `End Sub` lub `End Function`, `End Get`lub `End Set`, po ostatniej instrukcji treści procedury. Instrukcja `End` zwraca bezpośrednio kontrolę do kodu wywołującego. W procedurze można mieć tylko jedną instrukcję `End`.  
  
## <a name="parameters-and-arguments"></a>Parametry i argumenty  
 W większości przypadków procedura musi działać na różnych danych przy każdym wywołaniu. Te informacje można przekazać do procedury w ramach wywołania procedury. Procedura definiuje zero lub więcej *parametrów*, z których każdy reprezentuje wartość, która oczekuje na przekazanie do niej. Odpowiadający każdemu parametrowi w definicji procedury jest *argumentem* w wywołaniu procedury. Argument reprezentuje wartość przekazana do odpowiadającego mu parametru w danym wywołaniu procedury.  
  
## <a name="types-of-procedures"></a>Typy procedur  
 Visual Basic używa kilku typów procedur:  
  
- [Procedury Sub](./sub-procedures.md) wykonują akcje, ale nie zwracają wartości do kodu wywołującego.  
  
- Procedury obsługi zdarzeń są `Sub` procedurach, które są wykonywane w odpowiedzi na zdarzenie wywoływane przez akcję użytkownika lub przez wystąpienie w programie.  
  
- [Procedury funkcyjne](./function-procedures.md) zwracają wartość do kodu wywołującego. Mogą wykonać inne akcje przed zwróceniem.

    Niektóre funkcje zapisały C# zwracają *wartość zwracaną przez odwołanie*. Obiekty wywołujące funkcję mogą modyfikować wartość zwracaną, a ta modyfikacja jest odzwierciedlana w stanie wywoływanego obiektu. Począwszy od Visual Basic 2017, kod Visual Basic może korzystać z wartości zwracanych przez odwołanie, chociaż nie może zwracać wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania do zwracanych wartości](ref-return-values.md).
  
- [Procedury właściwości](./property-procedures.md) zwracają i przypisują wartości właściwości obiektów lub modułów.  
  
- [Procedury operatorów](./operator-procedures.md) definiują zachowanie operatora standardowego, gdy jeden lub oba operandy są nowo zdefiniowanymi klasami lub strukturą.  
  
- [Procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definiują jeden lub więcej *parametrów typu* oprócz ich zwykłych parametrów, dzięki czemu kod wywołujący może przekazać określone typy danych przy każdym wywołaniu.  
  
## <a name="procedures-and-structured-code"></a>Procedury i Kod strukturalny  
 Każdy wiersz kodu wykonywalnego w aplikacji musi znajdować się wewnątrz pewnej procedury, takiej jak `Main`, `calculate`lub `Button1_Click`. Jeśli dzieli się duże procedury na mniejsze, aplikacja jest bardziej czytelna.  
  
 Procedury są przydatne do wykonywania powtarzających się lub udostępnionych zadań, takich jak często używane obliczenia, manipulowanie tekstem i formantami oraz operacje bazy danych. Można wywołać procedurę z wielu różnych miejsc w kodzie, aby można było używać procedur jako bloków konstrukcyjnych dla aplikacji.  
  
 Tworzenie struktury kodu przy użyciu procedur zapewnia następujące korzyści:  
  
- Procedury umożliwiają podział programów na osobne jednostki logiczne. Można debugować osobne jednostki w łatwiejszy sposób, niż można debugować cały program bez procedur.  
  
- Po opracowaniu procedur do użycia w jednym programie można używać ich w innych programach, często z małą lub bez modyfikacji. Dzięki temu można uniknąć duplikowania kodu.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie procedury](./how-to-create-a-procedure.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
