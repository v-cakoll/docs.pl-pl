---
title: Używanie dyrektywy static- C# Reference
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 1a0e26d8b0a14e0c77b724fc492588e08762e47f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099998"
---
# <a name="using-static-directive-c-reference"></a>Używanie statycznej dyrektywyC# (odwołanie)

Dyrektywa `using static` wyznacza typ, którego statyczne składowe i zagnieżdżone typy można uzyskać dostęp bez określenia nazwy typu. Jego składnia to:

```csharp
using static <fully-qualified-type-name>;
```

gdzie w *pełni kwalifikowana nazwa* typu jest nazwą typu, którego statyczne składowe i zagnieżdżone typy mogą być wywoływane bez określenia nazwy typu. Jeśli nie podasz w pełni kwalifikowanej nazwy typu (pełna nazwa przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "nie można znaleźć nazwy typu lub przestrzeni nazw" typu/przestrzeni nazw "(czy nie brakuje dyrektywy using lub zestawu odwołanie?) ".

Dyrektywa `using static` ma zastosowanie do dowolnego typu, który ma statyczne elementy członkowskie (lub typy zagnieżdżone), nawet jeśli ma również elementy członkowskie wystąpienia. Jednak elementy członkowskie wystąpienia mogą być wywoływane tylko za pomocą wystąpienia typu.

Dyrektywa `using static` została wprowadzona w C# 6.

## <a name="remarks"></a>Uwagi

Zwykle podczas wywoływania statycznej składowej należy podać nazwę typu wraz z nazwą elementu członkowskiego. Wielokrotne wprowadzenie tej samej nazwy typu w celu wywołania elementów członkowskich typu może spowodować pełne, zaciemnienie kodu. Na przykład następująca definicja klasy `Circle` odwołuje się do wielu elementów członkowskich klasy <xref:System.Math>.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Eliminując konieczność jawnego odwoływania się do klasy <xref:System.Math> za każdym razem, gdy następuje odwołanie do elementu członkowskiego, dyrektywa `using static` tworzy wiele bardziej estetycznych kodu:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.  Dziedziczone elementy członkowskie nie są importowane.  Można importować z dowolnego typu nazwanego za pomocą dyrektywy static with, w tym modułów Visual Basic.  Jeśli F# funkcje najwyższego poziomu są wyświetlane w metadanych jako statyczne elementy członkowskie nazwanego typu, którego nazwa C# jest prawidłowym identyfikatorem, można zaimportować te F# funkcje.

 `using static` sprawia, że metody rozszerzające zadeklarowane w określonym typie są dostępne dla wyszukiwania metody rozszerzenia.  Jednak nazwy metod rozszerzenia nie są importowane do zakresu dla niekwalifikowanego odwołania w kodzie.

 Metody o tej samej nazwie zaimportowanej z różnych typów przez różne dyrektywy `using static` w tej samej jednostce kompilacji lub przestrzeni nazw tworzą grupę metod.  W ramach tych grup metod Rozpoznanie przeciążenia C# jest zgodne z normalnymi regułami.

## <a name="example"></a>Przykład

W poniższym przykładzie zastosowano dyrektywę `using static` w celu udostępnienia statycznych elementów członkowskich <xref:System.Console>, <xref:System.Math>i <xref:System.String>, bez konieczności określania ich nazwy typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

W przykładzie można także zastosować dyrektywę `using static` do typu <xref:System.Double>. Mogłoby to spowodować wywołanie metody <xref:System.Double.TryParse(System.String,System.Double@)> bez określenia nazwy typu. Jednak tworzy to mniej czytelny kod, ponieważ jest on niezbędny do sprawdzenia instrukcji `using static`, aby określić, który typ metody `TryParse` jest wywoływany.

## <a name="see-also"></a>Zobacz także

- [Using — dyrektywa](using-directive.md)
- [C#Odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
