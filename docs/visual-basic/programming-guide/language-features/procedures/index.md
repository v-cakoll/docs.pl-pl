---
title: Procedury w Visual Basic
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: 4b6dfe30268aef7dc61f130c2775e2cc0d1503e8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635630"
---
# <a name="procedures-in-visual-basic"></a>Procedury w Visual Basic
A *procedury* to blok instrukcji ujęta w instrukcji deklaracji (`Function`, `Sub`, `Operator`, `Get`, `Set`) i pasującą `End` deklaracji. Niektóre procedury musi być wszystkich instrukcji wykonywalnych w języku Visual Basic.  
  
## <a name="calling-a-procedure"></a>Wywoływanie procedury  
 Można wywołać procedury z innym miejscu w kodzie. Jest to nazywane *wywołanie procedury*. Po zakończeniu procedury uruchomiona, przekazuje sterowanie do kodu, który wywołana, i jest znany jako *wywoływanie kodu*. Kod wywołujący jest instrukcję lub wyrażenie w instrukcji, określa procedurę według nazwy, która przekazuje sterowanie do niego.  
  
## <a name="returning-from-a-procedure"></a>Zwracanie z procedury  
 Procedury zwraca kontrolę do kodu wywołującego, po zakończeniu działania. Aby to zrobić, można użyć [instrukcji Return](../../../../visual-basic/language-reference/statements/return-statement.md), odpowiednie [instrukcji zakończenia](../../../../visual-basic/language-reference/statements/exit-statement.md) poufności informacji dla procedury lub procedury [zakończenia \<— słowo kluczowe > instrukcji](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)instrukcji. Następnie sterowanie przechodzi do kodu wywołującego, zgodnie z pkt po wywołaniu procedury.  
  
- Za pomocą `Return` instrukcji, sterowanie powraca niezwłocznie do wywołującego kodu. Następujące instrukcje `Return` instrukcji nie działają. Masz więcej niż jedną `Return` instrukcji w tej samej procedury.  
  
- Za pomocą `Exit Sub` lub `Exit Function` instrukcji, sterowanie powraca niezwłocznie do wywołującego kodu. Następujące instrukcje `Exit` instrukcji nie działają. Masz więcej niż jedną `Exit` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit` instrukcje w tej samej procedury.  
  
- Jeśli nie ma procedury `Return` lub `Exit` instrukcji zawiera z `End Sub` lub `End Function`, `End Get`, lub `End Set` instrukcji następującej po ostatnim instrukcji treści procedury. `End` Instrukcja zwraca kontroli od razu do wywołującego kodu. Może mieć tylko jeden `End` instrukcji procedury.  
  
## <a name="parameters-and-arguments"></a>Parametry i argumenty  
 W większości przypadków procedura musi działać na różnych danych każdorazowo, należy wywołać. Te informacje można przekazać do procedury jako część wywołania procedury. Procedura określa zero lub więcej *parametry*, każdy z których reprezentuje wartość oczekuje przekazania do niej. Odpowiadający każdego parametru w definicji procedury jest *argument* w wywołaniu procedury. Argument reprezentuje wartość, które przekazujesz do odpowiedniego parametru w wywołaniu procedury danego.  
  
## <a name="types-of-procedures"></a>Rodzaje procedur  
 Visual Basic korzysta z kilku typów procedur:  
  
- [Procedury Sub](./sub-procedures.md) wykonywać działania, ale nie zwraca wartości do wywołującego kodu.  
  
- Procedury obsługi zdarzeń są `Sub` procedur, które są wykonywane w odpowiedzi na zdarzenie zgłaszane przez akcję użytkownika lub w przypadku wystąpienia w programie.  
  
- [Funkcja procedury](./function-procedures.md) zwracają wartość do wywołującego kodu. Przed zwróceniem mogli wykonywać inne czynności.

    Niektóre funkcje, napisany w C# zwracają *odwoływać się do wartości zwracanej*. Wywołań funkcji, można zmodyfikować zwracanej wartości, a ta zmiana jest odzwierciedlana w stan obiektu o nazwie. Począwszy od 2017 Visual Basic, kod języka Visual Basic mogą wykorzystywać wartości zwracane przez odwołanie, ale go nie może zwracać wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [wartości zwracane odwołanie](ref-return-values.md).
  
- [Procedury własności](./property-procedures.md) wróć i przypisać wartości właściwości do obiektów lub moduły.  
  
- [Procedury operatorów](./operator-procedures.md) Definiowanie zachowania standardowego operatora, gdy przynajmniej jeden z operandów jest nowo zdefiniowane przez klasę lub strukturę.  
  
- [Procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definiują jedną lub więcej *parametry typu* oprócz ich normalne parametrów, aby kod wywołujący może przekazać określone typy danych poszczególnych czasu nawiązuje połączenie.  
  
## <a name="procedures-and-structured-code"></a>Procedury składowane i węzeł strukturalny  
 Każdy wiersz kodu wykonywalnego w aplikacji musi znajdować się wewnątrz niektóre procedury, takich jak `Main`, `calculate`, lub `Button1_Click`. Jeśli dzielisz dużych procedury na mniejsze, aplikacja jest bardziej czytelne.  
  
 Procedury są przydatne w przypadku wykonywania powtórzonych lub udostępnione zadania, takie jak często używanych obliczeń, tekstu i sterującymi manipulacji i operacji w bazie danych. Możesz wywołać procedurę z wielu różnych miejsc w kodzie, dzięki czemu można użyć procedury jako bloków konstrukcyjnych dla aplikacji.  
  
 Tworzenie struktury kodu za pomocą procedury zapewnia następujące korzyści:  
  
- Procedury umożliwiają Podziel programów na osobne jednostki logiczne. Możesz łatwo debugować oddzielne zespoły więcej nie można debugować całego programu, bez procedur.  
  
- Po tworzenia procedur do użytku w jednym programie można ich używać w innych programów, często z niewielkich modyfikacji. Dzięki temu można uniknąć zduplikowania kodu.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie procedury](./how-to-create-a-procedure.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
