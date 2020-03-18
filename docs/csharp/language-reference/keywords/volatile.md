---
title: volatile — odwołanie do języka C#
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712848"
---
# <a name="volatile-c-reference"></a>volatile (odwołanie w C#)

Słowo `volatile` kluczowe wskazuje, że pole może być modyfikowane przez wiele wątków, które są wykonywane w tym samym czasie. Kompilator, system wykonywania, a nawet sprzęt może zmienić rozmieszczenie odczytów i zapisów w lokalizacjach pamięci ze względu na wydajność. Pola, które `volatile` są zadeklarowane nie podlegają tych optymalizacji. Dodanie `volatile` modyfikatora zapewnia, że wszystkie wątki będą obserwować lotnych zapisów wykonywanych przez inny wątek w kolejności, w jakiej zostały one wykonane. Nie ma żadnej gwarancji pojedynczej całkowitej kolejności nietrwałych zapisów, jak widać ze wszystkich wątków wykonywania.

Słowo `volatile` kluczowe można zastosować do pól tego typu:

- Typy odwołań.
- Typy wskaźników (w niebezpiecznym kontekście). Należy zauważyć, że chociaż sam wskaźnik może być lotny, obiekt, który wskazuje nie może. Innymi słowy nie można zadeklarować "wskaźnik do volatile."
- Proste typy, `sbyte` `byte`takie `short` `ushort`jak `int` `uint`, `char` `float`, `bool`, , , i .
- Typ `enum` z jednym z następujących `byte`typów `sbyte` `short`bazowych: , , `ushort`, `int`, lub `uint`.
- Ogólne parametry typu znane jako typy odwołań.
- <xref:System.IntPtr>i <xref:System.UIntPtr>.

Inne typy, `double` `long`w tym `volatile` i , nie mogą być oznaczone, ponieważ odczyty i zapisy pól tych typów nie mogą być zagwarantowane jako atomowej. Aby chronić dostęp wielowątkowy do tych typów <xref:System.Threading.Interlocked> pól, należy użyć [`lock`](lock-statement.md) elementów członkowskich klasy lub ochrony dostępu przy użyciu instrukcji.

Słowo `volatile` kluczowe można zastosować tylko do `class` `struct`pól lub . Nie można zadeklarować `volatile`zmiennych lokalnych .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `volatile`zadeklarować zmienną pola publicznego jako .

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

W poniższym przykładzie pokazano, jak można utworzyć wątek pomocniczy lub roboczy i wykorzystać do wykonywania przetwarzania równolegle z wątkiem podstawowym. Aby uzyskać więcej informacji na temat wielowątkowości, zobacz [Managed Threading](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

Po `volatile` dodaniu modyfikatora do deklaracji `_shouldStop` w miejscu, zawsze otrzymasz te same wyniki (podobne do fragmentu pokazanego w poprzednim kodzie). Jednak bez tego modyfikatora na `_shouldStop` element członkowski, zachowanie jest nieprzewidywalne. Metoda `DoWork` może zoptymalizować dostęp do elementu członkowskiego, co powoduje odczyt starych danych. Ze względu na charakter programowania wielowątkowego liczba starych odczytów jest nieprzewidywalna. Różne przebiegi programu będą dawać nieco inne wyniki.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Specyfikacja języka języka Języka Języka C#: volatile — słowo kluczowe](../../../../_csharplang/spec/classes.md#volatile-fields)
- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [instrukcja blokady](lock-statement.md)
- <xref:System.Threading.Interlocked>
