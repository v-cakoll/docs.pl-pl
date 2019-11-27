---
title: 'Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352905"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic

Należy zadeklarować zmienną [typu danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości (`=`) w instrukcji przypisania lub klauzuli inicjacji.

## <a name="example"></a>Przykład

Poniższy przykład deklaruje zmienną `Object` i przypisuje do niej bieżące wystąpienie.

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

- Odwołanie do przestrzeni nazw <xref:System>.

- Klasa, struktura lub moduł, w którym ma zostać umieszczona instrukcja `Dim`.

- Procedura, w której ma zostać umieszczona Instrukcja przypisania.

## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
