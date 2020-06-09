---
title: Używanie obiektów implementujących interfejs IDisposable
description: Dowiedz się, jak używać obiektów implementujących interfejs IDisposable w programie .NET. Typy korzystające z zasobów niezarządzanych implementują interfejs IDisposable, aby zezwalać na odzyskiwanie zasobów.
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 7d5d4080f22aab6870a230d495b4a4b9ebcb3b96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599857"
---
# <a name="using-objects-that-implement-idisposable"></a>Używanie obiektów implementujących interfejs IDisposable

Moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego ponownie przejmuje pamięć używaną przez zarządzane obiekty, ale typy korzystające z zasobów niezarządzanych implementują <xref:System.IDisposable> interfejs w celu zezwalania na odzyskiwanie zasobów wymaganych przez te niezarządzane zasoby. Po zakończeniu korzystania z obiektu, który implementuje <xref:System.IDisposable> , należy wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację obiektu. Można to zrobić na jeden z dwóch sposobów:

- Za pomocą instrukcji języka C# `using` ( `Using` w Visual Basic).
- Przez implementację `try/finally` bloku i wywołanie elementu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> w `finally` .

## <a name="the-using-statement"></a>Instrukcja using

[ `using` Instrukcja](../../csharp/language-reference/keywords/using-statement.md) w języku C# i [ `Using` instrukcja](../../visual-basic/language-reference/statements/using-statement.md) w Visual Basic upraszczają kod, który należy napisać, aby oczyścić obiekt. `using`Instrukcja uzyskuje jeden lub więcej zasobów, wykonuje określone instrukcje i automatycznie usuwa obiekt. Jednak `using` instrukcja jest przydatna tylko w przypadku obiektów, które są używane w zakresie metody, w której są zbudowane.

Poniższy przykład używa `using` instrukcji w celu utworzenia i zwolnienia <xref:System.IO.StreamReader?displayProperty=nameWithType> obiektu.

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

Mimo że <xref:System.IO.StreamReader> Klasa implementuje <xref:System.IDisposable> interfejs, który wskazuje, że używa niezarządzanego zasobu, przykład nie wywołuje jawnie <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody. Gdy kompilator języka C# lub Visual Basic napotka `using` instrukcję, emituje język pośredni (IL), który jest odpowiednikiem poniższego kodu, który jawnie zawiera `try/finally` blok.

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

Instrukcja języka C# `using` umożliwia także uzyskanie wielu zasobów w pojedynczej instrukcji, która jest wewnętrznie odpowiednikiem zagnieżdżonych `using` instrukcji. Poniższy przykład tworzy wystąpienie dwóch <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plików.

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Blok try/finally

Zamiast zawijać `try/finally` blok w `using` instrukcji, możesz wybrać opcję `try/finally` bezpośredniego wdrożenia bloku. Może to być osobisty styl kodowania lub można to zrobić z jednego z następujących powodów:

- Aby dołączyć `catch` blok obsługujący wyjątki zgłoszone w `try` bloku. W przeciwnym razie wyjątki zgłaszane w `using` instrukcji są nieobsługiwane.

- Aby utworzyć wystąpienie obiektu, który implementuje, <xref:System.IDisposable> którego zakres nie jest lokalny dla bloku, w którym jest zadeklarowany.

Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa `try/catch/finally` bloku do tworzenia wystąpienia, używania i usuwania <xref:System.IO.StreamReader> obiektu oraz do obsługi wszelkich wyjątków zgłoszonych przez <xref:System.IO.StreamReader> konstruktora i jego <xref:System.IO.StreamReader.ReadToEnd%2A> metodę. Kod w `finally` bloku sprawdza, czy obiekt, który implementuje <xref:System.IDisposable> nie `null` przed wywołaniem <xref:System.IDisposable.Dispose%2A> metody. Niewykonanie tej czynności może spowodować wyjątek w <xref:System.NullReferenceException> czasie wykonywania.

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

Możesz użyć tego podstawowego wzorca, jeśli zdecydujesz się zaimplementować lub musi zaimplementować `try/finally` blok, ponieważ język programowania nie obsługuje `using` instrukcji, ale zezwala na bezpośrednie wywołania <xref:System.IDisposable.Dispose%2A> metody.

## <a name="idisposable-instance-members"></a>Elementy członkowskie wystąpienia IDisposable

Jeśli klasa przechowuje <xref:System.IDisposable> implementację jako element członkowski wystąpienia, pole lub właściwość, należy również zaimplementować klasę <xref:System.IDisposable> . Aby uzyskać więcej informacji, zobacz [implementacja kaskadowego usuwania](implementing-dispose.md#cascade-dispose-calls).

## <a name="see-also"></a>Zobacz też

- [Oczyszczanie zasobów niezarządzanych](unmanaged.md)
- [using — Instrukcja (odwołanie w C#)](../../csharp/language-reference/keywords/using-statement.md)
- [Using — Instrukcja (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
