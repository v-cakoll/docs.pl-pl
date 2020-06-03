---
title: Używanie dyrektywy statycznej — odwołanie w C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: bffbc026e8f7937db91d42b7a06a5b7bba3bc2f8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396150"
---
# <a name="using-static-directive-c-reference"></a>Using static — dyrektywa (odwołanie w C#)

`using static`Dyrektywa określa typ, którego statyczne składowe i zagnieżdżone typy, do których można uzyskać dostęp bez określenia nazwy typu. Jego składnia to:

```csharp
using static <fully-qualified-type-name>;
```

gdzie w *pełni kwalifikowana nazwa* typu jest nazwą typu, którego statyczne składowe i zagnieżdżone typy mogą być wywoływane bez określenia nazwy typu. Jeśli nie podasz w pełni kwalifikowanej nazwy typu (pełna nazwa przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "nie można znaleźć nazwy typu lub przestrzeni nazw" typu/przestrzeni nazw "(czy nie brakuje dyrektywy using lub odwołania do zestawu?)".

`using static`Dyrektywa ma zastosowanie do dowolnego typu, który ma statyczne elementy członkowskie (lub typy zagnieżdżone), nawet jeśli ma również elementy członkowskie wystąpienia. Jednak elementy członkowskie wystąpienia mogą być wywoływane tylko za pomocą wystąpienia typu.

`using static`Dyrektywa została wprowadzona w języku C# 6.

## <a name="remarks"></a>Uwagi

Zwykle podczas wywoływania statycznej składowej należy podać nazwę typu wraz z nazwą elementu członkowskiego. Wielokrotne wprowadzenie tej samej nazwy typu w celu wywołania elementów członkowskich typu może spowodować pełne, zaciemnienie kodu. Na przykład następująca definicja `Circle` klasy odwołuje się do wielu elementów członkowskich <xref:System.Math> klasy.

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Eliminując konieczność jawnego odwoływania się do <xref:System.Math> klasy za każdym razem, gdy następuje odwołanie do elementu członkowskiego, `using static` dyrektywa generuje dużo kod czyszczący:

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`Importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.  Dziedziczone elementy członkowskie nie są importowane.  Można importować z dowolnego typu nazwanego za pomocą dyrektywy static with, w tym modułów Visual Basic.  Jeśli funkcje najwyższego poziomu języka F # są wyświetlane w metadanych jako statyczne elementy członkowskie nazwanego typu, którego nazwa jest prawidłowym identyfikatorem języka C#, można zaimportować funkcje języka F #.

 `using static`sprawia, że metody rozszerzające zadeklarowane w określonym typie są dostępne dla wyszukiwania metody rozszerzenia.  Jednak nazwy metod rozszerzenia nie są importowane do zakresu dla niekwalifikowanego odwołania w kodzie.

 Metody o tej samej nazwie zaimportowanej z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacji lub przestrzeni nazw tworzą grupę metod.  W ramach tych grup metod Rozpoznanie przeciążenia odbywa się zgodnie z normalnymi regułami języka C#.

## <a name="example"></a>Przykład

W poniższym przykładzie zastosowano `using static` dyrektywę, aby zapewnić statyczny element członkowski <xref:System.Console> <xref:System.Math> klas, i <xref:System.String> dostępnych bez konieczności określania ich nazwy typu.

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

W przykładzie `using static` można również zastosować dyrektywę do <xref:System.Double> typu. Mogłoby to umożliwić wywołanie <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określenia nazwy typu. Jednak tworzy to mniej czytelny kod, ponieważ jest konieczny do sprawdzenia `using static` dyrektywy w celu ustalenia, która metoda typu liczbowego `TryParse` jest wywoływana.

## <a name="see-also"></a>Zobacz też

- [Using — dyrektywa](using-directive.md)
- [Odwołanie w C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
