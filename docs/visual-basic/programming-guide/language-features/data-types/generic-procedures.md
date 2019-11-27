---
title: Procedury ogólne
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350083"
---
# <a name="generic-procedures-in-visual-basic"></a>Procedury ogólne w Visual Basic
*Procedura ogólna*, nazywana również *metodą rodzajową*, jest procedurą zdefiniowaną z co najmniej jednym parametrem typu. Dzięki temu kod wywołujący dostosowuje typy danych do swoich wymagań przy każdym wywołaniu procedury.  
  
 Procedura nie jest ogólna po prostu na mocy zdefiniowanej wewnątrz klasy generycznej lub struktury ogólnej. Aby być ogólny, procedura musi pobrać co najmniej jeden parametr typu, oprócz wszystkich normalnych parametrów, które może podjąć. Ogólna Klasa lub struktura może zawierać procedury nieogólne, a niegeneryczna Klasa, struktura lub moduł mogą zawierać procedury ogólne.  
  
 Procedura ogólna może używać jej parametrów typu na swojej normalnej liście parametrów, w jej typie zwracanym, jeśli ma jeden, i w jego kodzie procedury.  
  
## <a name="type-inference"></a>Wnioskowanie o typie  
 Można wywołać procedurę ogólną bez podawania żadnych argumentów typu. Jeśli wywołasz ten sposób, kompilator próbuje określić odpowiednie typy danych do przekazania do argumentów typu procedury. Jest to nazywane *wnioskami o typie*. Poniższy kod pokazuje wywołanie, w którym kompilator uważa, że powinien przekazać typ `String` do `t`parametru typu.  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 Jeśli kompilator nie może wywnioskować argumentów typu z kontekstu wywołania, zgłosi błąd. Jedną z możliwych przyczyn tego błędu jest niezgodność rangi tablicy. Załóżmy na przykład, że definiujesz normalny parametr jako tablicę parametru typu. W przypadku wywołania procedury ogólnej dostarczającej tablicę o innej rangi (liczbie wymiarów) niezgodność powoduje niepowodzenie wnioskowania o typie. Poniższy kod pokazuje wywołanie, w którym tablica dwuwymiarowa jest przekazana do procedury, która oczekuje tablicy jednowymiarowej.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Wnioskowanie o typie można wywołać tylko poprzez pominięcie wszystkich argumentów typu. W przypadku podania jednego typu argumentu należy podać wszystkie.  
  
 Wnioskowanie o typie jest obsługiwane tylko dla procedur ogólnych. Nie można wywołać wnioskowania o typie dla klas ogólnych, struktur, interfejsów ani delegatów.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład definiuje ogólną procedurę `Function`, aby znaleźć konkretny element w tablicy. Definiuje jeden parametr typu i używa go do konstruowania dwóch parametrów na liście parametrów.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Komentarze  
 Poprzedni przykład wymaga możliwości porównania `searchValue` z każdym elementem `searchArray`. Aby zagwarantować tę możliwość, ogranicza parametr typu `T` w celu zaimplementowania interfejsu <xref:System.IComparable%601>. Kod używa metody <xref:System.IComparable%601.CompareTo%2A> zamiast operatora `=`, ponieważ nie ma gwarancji, że argument typu dostarczony dla `T` obsługuje operatora `=`.  
  
 Procedurę `findElement` można przetestować przy użyciu następującego kodu.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 Poprzednie wywołania `MsgBox` wyświetlają odpowiednio wartości "0", "1" i "-1".  
  
## <a name="see-also"></a>Zobacz także

- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Instrukcje: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry i argumenty procedur](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Lista typów](../../../../visual-basic/language-reference/statements/type-list.md)
- [Lista parametrów](../../../../visual-basic/language-reference/statements/parameter-list.md)
