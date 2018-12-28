---
title: za pomocą instrukcji - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: df116a200795fd20405381fd71e82d1d6fe662bc
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614392"
---
# <a name="using-statement-c-reference"></a>Using — instrukcja (C# odwołania)

Miejsce wygodnej składni, która zapewnia prawidłowe użycie <xref:System.IDisposable> obiektów.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `using` instrukcji.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a>Uwagi

<xref:System.IO.File> i <xref:System.Drawing.Font> to przykłady typów zarządzanych, uzyskujących dostęp do niezarządzanych zasobów (w tym dojścia do plików wielkości liter i konteksty urządzenia). Istnieje wiele innych rodzajów zasobów niezarządzanych i typy biblioteki klas, które hermetyzują je. Typy takie musi implementować <xref:System.IDisposable> interfejsu.

Gdy okres istnienia `IDisposable` obiektu jest ograniczona do jednej metody, należy zadeklarować i Utwórz wystąpienie w `using` instrukcji. `using` Instrukcja wywołuje <xref:System.IDisposable.Dispose%2A> metody na obiekt w prawidłowy sposób i (Jeśli używasz tego jak pokazano wcześniej) powoduje także sam wykraczać poza zakres obiekt zaraz <xref:System.IDisposable.Dispose%2A> jest wywoływana. W ramach `using` bloku, obiekt jest tylko do odczytu i nie można zmodyfikować ani ponownie przypisane.

`using` Instrukcji zapewnia, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek w obrębie `using` bloku. Ten sam efekt można osiągnąć, umieszczając w obiekcie wewnątrz właściwości `try` bloku, a następnie wywołując <xref:System.IDisposable.Dispose%2A> w `finally` zablokować; w rzeczywistości jest to sposób, w jaki `using` instrukcji jest tłumaczony przez kompilator. W przykładzie kodu wcześniej rozwija następujący kod w czasie kompilacji (Uwaga: bardzo nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu "):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Aby uzyskać więcej informacji na temat `try` - `finally` poufności informacji, zobacz [try-finally](try-finally.md) tematu.

Wiele wystąpień tego typu może być zadeklarowana w `using` instrukcji, jak pokazano w poniższym przykładzie:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Można utworzyć wystąpienia obiektu zasobu, a następnie przekaż zmienną `using` instrukcji, ale nie jest najlepszym rozwiązaniem. W takim przypadku po liście kontroli `using` zablokować, pozostaje obiekt w zakresie, ale prawdopodobnie nie ma dostępu do niezarządzanych zasobów. Innymi słowy nie są w pełni inicjalizacji dłużej. Jeśli spróbujesz użyć obiektu poza `using` zablokować ryzyka powoduje zgłoszenie wyjątku. Z tego powodu zaleca ogólnie do utworzenia wystąpienia obiektu w `using` instrukcji i jego zakres, aby ograniczyć `using` bloku.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Aby uzyskać więcej informacji na temat usuwania `IDisposable` obiekty, zobacz [używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](~/_csharplang/spec/statements.md#the-using-statement) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [using, dyrektywa](using-directive.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
- [Używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interfejs IDisposable](xref:System.IDisposable)