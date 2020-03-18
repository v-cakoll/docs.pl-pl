---
title: using statement - C# Odwołanie
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712965"
---
# <a name="using-statement-c-reference"></a>using statement (C# Reference)

Zapewnia wygodną składnię, która <xref:System.IDisposable> zapewnia prawidłowe użycie obiektów.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `using` instrukcji.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

Począwszy od języka C# 8.0, można użyć `using` następującej alternatywnej składni dla instrukcji, która nie wymaga nawiasów klamrowych:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Uwagi

<xref:System.IO.File>i <xref:System.Drawing.Font> są przykładami typów zarządzanych, które uzyskują dostęp do zasobów niezarządzanych (w tym przypadku dojścia do plików i kontekstów urządzeń). Istnieje wiele innych rodzajów zasobów niezarządzanych i typów bibliotek klas, które je hermetyzują. Wszystkie takie typy <xref:System.IDisposable> muszą implementować interfejs.

Gdy okres istnienia `IDisposable` obiektu jest ograniczona do jednej metody, należy zadeklarować i utworzyć wystąpienia w `using` instrukcji. Instrukcja `using` wywołuje <xref:System.IDisposable.Dispose%2A> metodę na obiekcie w prawidłowy sposób i (gdy używasz go, jak pokazano wcześniej) powoduje <xref:System.IDisposable.Dispose%2A> również, że sam obiekt, aby przejść poza zakres, jak tylko zostanie wywołana. W `using` bloku obiekt jest tylko do odczytu i nie można go modyfikować ani ponownie przypisywać.

Instrukcja `using` zapewnia, <xref:System.IDisposable.Dispose%2A> że jest wywoływana, `using` nawet jeśli wystąpi wyjątek w bloku. Ten sam wynik można osiągnąć, umieszczając `try` obiekt wewnątrz <xref:System.IDisposable.Dispose%2A> bloku, a następnie wywołując w `finally` bloku; w rzeczywistości jest to, jak instrukcja `using` jest tłumaczona przez kompilator. Przykład kodu wcześniej rozszerza się do następującego kodu w czasie kompilacji (zwróć uwagę na dodatkowe nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Nowsza `using` składnia instrukcji przekłada się na bardzo podobny kod. Blok `try` zostanie otwarty, gdzie zmienna jest zadeklarowana. Blok `finally` jest dodawany na zamknięciu otaczającego bloku, zazwyczaj na końcu metody.

Aby uzyskać więcej `try` - `finally` informacji na temat instrukcji, zobacz temat [try-finally.](try-finally.md)

Wiele wystąpień typu można zadeklarować `using` w instrukcji, jak pokazano w poniższym przykładzie:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Można połączyć wiele deklaracji tego samego typu przy użyciu nowej składni wprowadzone z C# 8, jak również. Jest to pokazane w poniższym przykładzie:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Można utworzyć wystąpienia obiektu zasobu, a następnie `using` przekazać zmienną do instrukcji, ale nie jest to najlepsze rozwiązanie. W takim przypadku po `using` kontroli opuszcza blok, obiekt pozostaje w zakresie, ale prawdopodobnie nie ma dostępu do jego zasobów niezarządzanych. Innymi słowy, nie jest już w pełni zainicjowany. Jeśli spróbujesz użyć `using` obiektu poza blokiem, istnieje ryzyko, powodując wyjątek. Z tego powodu zazwyczaj lepiej jest utworzyć wystąpienia obiektu w `using` instrukcji i ograniczyć `using` jego zakres do bloku.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Aby uzyskać więcej informacji `IDisposable` na temat usuwania obiektów, zobacz [Korzystanie z obiektów, które implementują IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Using instrukcji](~/_csharplang/spec/statements.md#the-using-statement) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [using, dyrektywa](using-directive.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
- [Korzystanie z obiektów implementujących IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interfejs IDisposable](xref:System.IDisposable)
- [używanie instrukcji w języku C# 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
