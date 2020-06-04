---
title: 'Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410506"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic

Należy zadeklarować zmienną [typu danych obiektu](../../../language-reference/data-types/object-data-type.md) przez określenie `As Object` w [instrukcji Dim](../../../language-reference/statements/dim-statement.md). Obiekt można przypisać do takiej zmiennej poprzez umieszczenie obiektu po znaku równości ( `=` ) w instrukcji przypisania lub klauzuli inicjującej.

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

## <a name="compile-the-code"></a>Kompiluj kod

Ten przykład wymaga:

- Odwołanie do <xref:System> przestrzeni nazw.

- Klasa, struktura lub moduł, w którym należy umieścić `Dim` instrukcję.

- Procedura, w której ma zostać umieszczona Instrukcja przypisania.

## <a name="see-also"></a>Zobacz też

- [Deklaracja zmiennej](variable-declaration.md)
- [Zmienne obiektów](object-variables.md)
- [Deklaracja zmiennej obiektu](object-variable-declaration.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
- [Dim, instrukcja](../../../language-reference/statements/dim-statement.md)
- [Wnioskowanie o typie lokalnym](local-type-inference.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
