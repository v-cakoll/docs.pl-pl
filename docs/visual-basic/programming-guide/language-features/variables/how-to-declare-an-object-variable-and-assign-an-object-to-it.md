---
title: 'Instrukcje: Zadeklaruj zmienną obiektu i przypisz do niej obiekt w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630873"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Instrukcje: Zadeklaruj zmienną obiektu i przypisz do niej obiekt w Visual Basic

Należy zadeklarować zmienną [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) przez określenie `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości (`=`) w instrukcji przypisania lub klauzuli inicjującej.

## <a name="example"></a>Przykład

Poniższy przykład deklaruje `Object` zmienną i przypisuje do niej bieżące wystąpienie.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Deklarację i przypisanie można połączyć przez zainicjowanie zmiennej jako części swojej deklaracji. Poniższy przykład jest równoważny z poprzednim przykładem.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Odwołanie do <xref:System> przestrzeni nazw.

- Klasa, struktura lub moduł, w którym należy umieścić `Dim` instrukcję.

- Procedura, w której ma zostać umieszczona Instrukcja przypisania.

## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
