---
title: Nazwę zmiennej zakresu można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6b155de0bb62f667ca76ec9454dec1466976a9b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400412"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Nazwę zmiennej zakresu można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów

Element programistyczny, który ma co najmniej jeden argument jest dołączony do zapytania LINQ. Kompilator nie może wywnioskować zmiennej zakresu z tego elementu programowania.

**Identyfikator błędu:** BC36599

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Podaj jawną nazwę zmiennej dla elementu programistycznego, jak pokazano w poniższym kodzie:

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [SELECT — klauzula](../queries/select-clause.md)
