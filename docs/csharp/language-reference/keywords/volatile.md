---
title: volatile — C# odwołanie
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: e72173ba1b91f03ccb1c15ca6451ac997666bc7f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422129"
---
# <a name="volatile-c-reference"></a>volatile (odwołanie w C#)

Słowo kluczowe `volatile` wskazuje, że pole może być modyfikowane przez wiele wątków, które są wykonywane w tym samym czasie. Kompilator, system środowiska uruchomieniowego i nawet sprzęt mogą zmieniać rozmieszczenie odczytów i zapisów w lokalizacjach pamięci ze względu na wydajność. Pola, które są zadeklarowane `volatile` nie podlegają tym optymalizacji. Dodanie modyfikatora `volatile` gwarantuje, że wszystkie wątki będą obserwować nietrwałe zapisy wykonywane przez dowolny wątek w kolejności, w której zostały wykonane. Nie istnieje gwarancja pojedynczej kolejności zapisów nietrwałych w postaci zaobserwowanej ze wszystkich wątków wykonania.

Słowo kluczowe `volatile` można zastosować do pól tych typów:

- Typy odwołań.
- Typy wskaźnika (w niebezpiecznym kontekście). Należy zauważyć, że chociaż wskaźnik może być nietrwały, obiekt, do którego wskazuje element, nie może. Innymi słowy, nie można zadeklarować "wskaźnika do nietrwałego".
- Typy proste, takie jak `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`i `bool`.
- Typ `enum` z jednym z następujących typów podstawowych: `byte`, `sbyte`, `short`, `ushort`, `int`lub `uint`.
- Parametry typu ogólnego znane jako typy referencyjne.
- <xref:System.IntPtr> i <xref:System.UIntPtr>.

Inne typy, w tym `double` i `long`, nie mogą być oznaczone jako `volatile` ponieważ operacje odczytu i zapisu do pól tych typów nie mogą być niepodzielne. Aby chronić wielowątkowy dostęp do tych typów pól, Użyj elementów członkowskich klasy <xref:System.Threading.Interlocked> lub Włącz ochronę dostępu przy użyciu instrukcji [`lock`](lock-statement.md) .

Słowo kluczowe `volatile` może być stosowane tylko do pól `class` lub `struct`. Nie można zadeklarować zmiennych lokalnych `volatile`.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować zmienną pola publicznego jako `volatile`.

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

W poniższym przykładzie pokazano, jak można utworzyć wątek pomocniczy lub proces roboczy, który będzie używany do przetwarzania równolegle z elementem wątku głównego. Aby uzyskać więcej informacji na temat wielowątkowości, zobacz [zarządzane wątki](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

Po dodaniu modyfikatora `volatile` do deklaracji `_shouldStop` na miejscu zawsze uzyskasz te same wyniki (podobnie jak w powyższym fragmencie kodu). Jednak bez tego modyfikatora dla elementu członkowskiego `_shouldStop` zachowanie jest nieprzewidywalne. Metoda `DoWork` może zoptymalizować dostęp do elementu członkowskiego, co spowoduje odczytanie starych danych. Ze względu na charakter programowania wielowątkowego liczba nieodświeżonych odczytów jest nieprzewidywalne. Różne uruchomienia programu będą dawać nieco inne wyniki.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Specyfikacja języka: słowo kluczowe volatile](../../../../_csharplang/spec/classes.md#volatile-fields)
- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [lock — Instrukcja](lock-statement.md)
- <xref:System.Threading.Interlocked>
