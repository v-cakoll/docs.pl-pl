---
title: 'Zarządzanie zasobami: use — Słowo kluczowe (F#)'
description: 'Więcej informacji na temat języka F # — słowo kluczowe "use" i "przy użyciu" funkcji, która może kontrolować inicjowania i zwolnienia zasobów.'
ms.date: 05/16/2016
ms.openlocfilehash: c75783080d1d87c6ee75aede500d3d0b3fdf8355
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-management-the-use-keyword"></a>Zarządzanie zasobami: use — Słowo kluczowe

W tym temacie opisano kluczowego `use` i `using` funkcji, która może kontrolować inicjowania i zwolnienia zasobów.

## <a name="resources"></a>Zasoby
Termin *zasobów* są używane w więcej niż jeden sposób. Tak, zasoby mogą być danych przy użyciu aplikacji, takich jak ciągów, grafiki i podobne, ale w tym kontekście *zasobów* odwołuje się do zasobów oprogramowania lub systemu operacyjnego, takie jak konteksty urządzenia grafiki, dojścia do plików w sieci i bazy danych połączenia, współbieżności obiekty, takie jak uchwyty oczekiwania i tak dalej. Korzystanie z tych zasobów przez aplikacje obejmuje nabywania zasobów z system operacyjny lub inne dostawcy zasobów, a następnie w nowszej wersji zasobu do puli, dzięki czemu może zostać dostarczona do innej aplikacji. Problemy występują, jeśli aplikacje nie zwalnia wspólnej puli zasobów.

## <a name="managing-resources"></a>Zarządzanie zasobami
Aby wydajnie i odpowiedzialne zarządzać zasobami w aplikacji, należy zwolnić zasoby szybko i w sposób przewidywalny. .NET Framework ułatwia to zrobić, podając `System.IDisposable` interfejsu. Typ, który implementuje `System.IDisposable` ma `System.IDisposable.Dispose` metodę, która poprawnie zwalnia zasoby. Dobrze napisanych aplikacji zagwarantować, że `System.IDisposable.Dispose` jest wywoływana natychmiast po każdym obiekcie, który przechowuje ograniczonych zasobów nie są już potrzebne. Na szczęście większość języków .NET obsługuje ułatwić, i F # nie jest wyjątkiem. Istnieją dwa konstrukcji języka przydatne, które obsługują wzorzec dispose: `use` powiązania i `using` funkcji.

## <a name="use-binding"></a>Użyj powiązania
`use` — Słowo kluczowe ma formę, przypominający `let` powiązania:

Użyj *wartość* = *wyrażenia*

Zapewnia te same funkcje co `let` powiązania, ale dodaje wywołanie `Dispose` na wartość, jeśli wartość wykracza poza zakres. Należy pamiętać, że kompilator wstawia sprawdzania wartości null dla wartości, tak, że jeśli wartość jest `null`, wywołanie `Dispose` nie jest wykonywane.

Poniższy przykład przedstawia sposób automatycznie zamknąć plik za pomocą `use` — słowo kluczowe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Można użyć `use` w wyrażeniach obliczeń, w którym to przypadku dostosowaną wersję `use` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).


## <a name="using-function"></a>przy użyciu funkcji
`using` Funkcja ma następujący format:

`using` (*wyrażenie1*) *funkcji lub lambda*

W `using` wyrażenie *wyrażenie1* tworzy obiekt, który musi zostać usunięty. Wynik *wyrażenie1* (obiekt, który musi zostać usunięty) staje się argument *wartość*, do *funkcji lub lambda*, która jest funkcja, która oczekuje pojedynczy pozostały argumentu typu, która jest zgodna z wartością utworzonego przez *wyrażenie1*, lub wyrażenie lambda, które oczekuje argumentu typu. Po zakończeniu wykonywania funkcji wymaga środowiska uruchomieniowego `Dispose` i zwalnia zasoby (chyba, że wartość jest `null`, w którym to przypadku nie jest wykonywane wywołanie metody Dispose).

W poniższym przykładzie pokazano `using` wyrażenie za pomocą wyrażenia lambda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

W następnym przykładzie pokazano `using` wyrażenie przy użyciu funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Należy pamiętać, że funkcja może być funkcję, która zawiera niektóre argumenty już stosowane. W poniższym przykładzie kodu pokazano to. Tworzy plik, który zawiera ciąg `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Funkcji i `use` powiązania są prawie równoważne sposobów, aby osiągnąć ten sam efekt. `using` — Słowo kluczowe zapewnia większą kontrolę nad tym, kiedy `Dispose` jest wywoływana. Jeśli używasz `using`, `Dispose` jest wywoływane na końcu wyrażenia funkcji lub lambda, gdy używasz `use` — słowo kluczowe, `Dispose` jest wywoływana po zakończeniu zawierający go blok kodu. Ogólnie rzecz biorąc, powinien wolisz użyć `use` zamiast `using` funkcji.


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)
