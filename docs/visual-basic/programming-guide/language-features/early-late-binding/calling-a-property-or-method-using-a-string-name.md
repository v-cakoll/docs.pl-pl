---
title: Wywoływanie właściwości lub metody za pomocą nazwy ciągu
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: cb584f0dfbd905ca071f9a86b1eab231f3017538
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345208"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Wywoływanie właściwości lub metody za pomocą nazwy ciągu (Visual Basic)
W większości przypadków można odkrywać właściwości i metody obiektu w czasie projektowania i pisać kod, aby je obsłużyć. Niemniej jednak w niektórych przypadkach można nie wiedzieć o właściwościach i metodach obiektu z wyprzedzeniem, a także zapewnić elastyczność umożliwiającą użytkownikom końcowym Określanie właściwości lub metod wykonywania w czasie wykonywania.  
  
## <a name="callbyname-function"></a>CallByName — funkcja  
 Rozważmy na przykład aplikację kliencką, która oblicza wyrażenia wprowadzone przez użytkownika przez przekazanie operatora do składnika modelu COM. Załóżmy, że stale dodajemy nowe funkcje do składnika wymagającego nowych operatorów. W przypadku korzystania ze standardowych technik dostępu do obiektów należy ponownie skompilować i ponownie rozpowszechnić aplikację kliencką przed użyciem nowych operatorów. Aby tego uniknąć, można użyć funkcji `CallByName`, aby przekazać nowe operatory jako ciągi, bez zmiany aplikacji.  
  
 Funkcja `CallByName` umożliwia użycie ciągu do określenia właściwości lub metody w czasie wykonywania. Sygnatura funkcji `CallByName` wygląda następująco:  
  
 *Wynik* = `CallByName`(*Object*, *procedurname*, *CallType*, *arguments*())  
  
 Pierwszy argument, *obiekt*, przyjmuje nazwę obiektu, na którym ma być wykonywane działanie. Argument MethodName przyjmuje ciąg, który zawiera nazwę metody lub właściwości, która ma zostać wywołana. Argument *CallType* przyjmuje stałą reprezentującą typ procedury do wywołania: metodę (`Microsoft.VisualBasic.CallType.Method`), właściwość read (`Microsoft.VisualBasic.CallType.Get`) lub zestaw właściwości (`Microsoft.VisualBasic.CallType.Set`). Argument arguments, który jest opcjonalny, pobiera tablicę typu `Object`, która zawiera argumenty do procedury.  
  
 Możesz użyć `CallByName` z klasami w bieżącym rozwiązaniu, ale jest to najczęściej używane do uzyskiwania dostępu do obiektów COM lub obiektów z zestawów .NET Framework.  
  
 Załóżmy, że dodasz odwołanie do zestawu, który zawiera klasę o nazwie `MathClass`, która ma nową funkcję o nazwie `SquareRoot`, jak pokazano w poniższym kodzie:  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Aplikacja może używać kontrolek pól tekstowych do kontrolowania, która metoda zostanie wywołana i jej argumentów. Na przykład jeśli `TextBox1` zawiera wyrażenie do obliczenia, a `TextBox2` służy do wprowadzania nazwy funkcji, można użyć następującego kodu do wywołania funkcji `SquareRoot` w wyrażeniu w `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 Jeśli wprowadzisz wartość "64" w `TextBox1`, "SquareRoot" w `TextBox2`, a następnie wywołamy procedurę `CallMath`, zostanie obliczony pierwiastek kwadratowy liczby w `TextBox1`. Kod w przykładzie wywołuje funkcję `SquareRoot` (która pobiera ciąg zawierający wyrażenie, które ma być oceniane jako argument wymagany) i zwraca wartość "8" w `TextBox1` (pierwiastek kwadratowy 64). Oczywiście, jeśli użytkownik wprowadzi nieprawidłowy ciąg w `TextBox2`, jeśli ciąg zawiera nazwę właściwości zamiast metody lub jeśli metoda miała dodatkowy argument wymagany, wystąpi błąd czasu wykonywania. Musisz dodać niezawodny kod obsługi błędów, gdy używasz `CallByName`, aby przewidzieć te lub wszystkie inne błędy.  
  
> [!NOTE]
> Chociaż funkcja `CallByName` może być przydatna w niektórych przypadkach, należy zaważyć jej użyteczność przed wpływem na wydajność — użycie `CallByName` do wywołania procedury jest nieco wolniejsze niż w przypadku wywołania z późnym wiązaniem. Jeśli wywołujesz funkcję, która jest wywoływana wielokrotnie, na przykład wewnątrz pętli, `CallByName` może mieć silny wpływ na wydajność.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Określanie typu obiektu](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
