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
ms.openlocfilehash: 2efc0410b9d4bb663e1ff19d5a5456d7ff2c99bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394068"
---
# <a name="generic-procedures-in-visual-basic"></a>Procedury ogólne w Visual Basic
*Procedura ogólna*, nazywana również *metodą rodzajową*, jest procedurą zdefiniowaną z co najmniej jednym parametrem typu. Dzięki temu kod wywołujący dostosowuje typy danych do swoich wymagań przy każdym wywołaniu procedury.  
  
 Procedura nie jest ogólna po prostu na mocy zdefiniowanej wewnątrz klasy generycznej lub struktury ogólnej. Aby być ogólny, procedura musi pobrać co najmniej jeden parametr typu, oprócz wszystkich normalnych parametrów, które może podjąć. Ogólna Klasa lub struktura może zawierać procedury nieogólne, a niegeneryczna Klasa, struktura lub moduł mogą zawierać procedury ogólne.  
  
 Procedura ogólna może używać jej parametrów typu na swojej normalnej liście parametrów, w jej typie zwracanym, jeśli ma jeden, i w jego kodzie procedury.  
  
## <a name="type-inference"></a>Wnioskowanie o typie  
 Można wywołać procedurę ogólną bez podawania żadnych argumentów typu. Jeśli wywołasz ten sposób, kompilator próbuje określić odpowiednie typy danych do przekazania do argumentów typu procedury. Jest to nazywane *wnioskami o typie*. Poniższy kod pokazuje wywołanie, w którym kompilator uważa, że powinien przekazywać typ `String` do parametru typu `t` .  
  
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
 W poniższym przykładzie zdefiniowano procedurę ogólną, `Function` Aby znaleźć konkretny element w tablicy. Definiuje jeden parametr typu i używa go do konstruowania dwóch parametrów na liście parametrów.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Komentarze  
 Poprzedni przykład wymaga możliwości porównania z `searchValue` każdym elementem `searchArray` . Aby zagwarantować tę możliwość, ogranicza parametr typu `T` w celu zaimplementowania <xref:System.IComparable%601> interfejsu. Kod używa <xref:System.IComparable%601.CompareTo%2A> metody zamiast `=` operatora, ponieważ nie ma gwarancji, że argument typu dostarczony dla `T` obsługuje `=` operatora.  
  
 Procedurę można przetestować `findElement` przy użyciu następującego kodu.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 Poprzednie wywołania do `MsgBox` wyświetlania odpowiednio wartości "0", "1" i "-1".  
  
## <a name="see-also"></a>Zobacz też

- [Typy ogólne w Visual Basic](generic-types.md)
- [Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Instrukcje: Używanie klasy ogólnej](how-to-use-a-generic-class.md)
- [Procedury](../procedures/index.md)
- [Parametry i argumenty procedur](../procedures/procedure-parameters-and-arguments.md)
- [Lista typów](../../../language-reference/statements/type-list.md)
- [Lista parametrów](../../../language-reference/statements/parameter-list.md)
