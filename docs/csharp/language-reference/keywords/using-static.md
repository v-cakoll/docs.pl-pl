---
title: przy użyciu dyrektywy statycznej - C# Reference
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712952"
---
# <a name="using-static-directive-c-reference"></a>przy użyciu dyrektywy statycznej (C# Reference)

Dyrektywa `using static` wyznacza typ, którego statyczne elementy członkowskie i typy zagnieżdżone można uzyskać dostęp bez określania nazwy typu. Jego składnia jest:

```csharp
using static <fully-qualified-type-name>;
```

gdzie *w pełni kwalifikowana nazwa typu* jest nazwą typu, do którego można odwoływać się do statycznych elementów członkowskich i typów zagnieżdżonych bez określania nazwy typu. Jeśli nie podasz w pełni kwalifikowaną nazwę typu (pełna nazwa obszaru nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246:](../compiler-messages/cs0246.md)"Nie można odnaleźć nazwy typu lub obszaru nazw "typ/obszar nazw" (brakuje ci using dyrektywy lub odwołania do zestawu?)".

Dyrektywa `using static` ma zastosowanie do dowolnego typu, który ma statycznych elementów członkowskich (lub typów zagnieżdżonych), nawet jeśli ma również elementy członkowskie wystąpienia. Jednak elementy członkowskie wystąpienia można wywołać tylko za pośrednictwem wystąpienia typu.

Dyrektywa `using static` została wprowadzona w języku C# 6.

## <a name="remarks"></a>Uwagi

Zwykle podczas wywoływania statycznego elementu członkowskiego podajesz nazwę typu wraz z nazwą elementu członkowskiego. Wielokrotne wprowadzanie tej samej nazwy typu w celu wywołania elementów członkowskich typu może spowodować pełne, niejasne kodu. Na przykład następująca definicja `Circle` klasy odwołuje się <xref:System.Math> do liczby członków klasy.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Poprzez wyeliminowanie konieczności jawnie <xref:System.Math> odwoływać się do klasy za `using static` każdym razem odwołuje się do elementu członkowskiego, dyrektywa tworzy znacznie czystszy kod:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`importuje dostępne tylko elementy statyczny i typy zagnieżdżone zadeklarowane w określonym typie.  Dziedziczone elementy członkowskie nie są importowane.  Można zaimportować z dowolnego typu o nazwie za pomocą dyrektywy statycznej, w tym modułów języka Visual Basic.  Jeśli f# funkcje najwyższego poziomu pojawiają się w metadanych jako statyczne elementy członkowskie nazwanego typu, którego nazwa jest prawidłowy identyfikator C#, a następnie F# funkcje mogą być importowane.

 `using static`sprawia, że metody rozszerzenia zadeklarowane w określonym typie są dostępne do wyszukiwania metody rozszerzenia.  Jednak nazwy metod rozszerzenia nie są importowane do zakresu dla niekwalifikowanego odwołania w kodzie.

 Metody o tej samej nazwie importowane `using static` z różnych typów przez różne dyrektywy w tej samej jednostce kompilacji lub przestrzeni nazw tworzą grupę metod.  Rozpoznawanie przeciążenia w ramach tych grup metod jest zgodne z normalnymi regułami Języka C#.

## <a name="example"></a>Przykład

W `using static` poniższym przykładzie użyto dyrektywy, <xref:System.Console> <xref:System.Math>aby <xref:System.String> statyczne elementy członkowskie , i klasy dostępne bez konieczności określania ich nazwy typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

W tym przykładzie `using static` dyrektywy można również zastosować <xref:System.Double> do typu. Umożliwiłoby to wywołanie <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu. Jednak to tworzy mniej czytelny kod, ponieważ staje `using static` się konieczne, aby sprawdzić `TryParse` instrukcje, aby określić, która metoda typu liczbowego jest wywoływana.

## <a name="see-also"></a>Zobacz też

- [za pomocą dyrektywy](using-directive.md)
- [Odwołanie do języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
