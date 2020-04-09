---
title: using statement - Odwołanie do języka C#
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989184"
---
# <a name="using-statement-c-reference"></a>przy użyciu instrukcji (odwołanie w języku C#)

Zapewnia wygodną składnię, która zapewnia <xref:System.IDisposable> prawidłowe użycie obiektów. Począwszy od języka C# 8.0, instrukcja `using` zapewnia poprawne użycie <xref:System.IAsyncDisposable> obiektów.

## <a name="example"></a>Przykład

W poniższym przykładzie `using` pokazano, jak używać instrukcji.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

Począwszy od języka C# 8.0, można użyć `using` następującej alternatywnej składni dla instrukcji, która nie wymaga nawiasów klamrowych:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Uwagi

<xref:System.IO.File>i <xref:System.Drawing.Font> są przykładami typów zarządzanych, które uzyskują dostęp do zasobów niezarządzanych (w tym przypadku dojścia do pliku i konteksty urządzenia). Istnieje wiele innych rodzajów zasobów niezarządzanych i typów bibliotek klas, które je hermetyzują. Wszystkie takie typy <xref:System.IDisposable> muszą implementować interfejs lub <xref:System.IAsyncDisposable> interfejs.

Gdy okres istnienia `IDisposable` obiektu jest ograniczona do pojedynczej metody, należy zadeklarować i utworzyć wystąpienia go w `using` instrukcji. Instrukcja `using` wywołuje <xref:System.IDisposable.Dispose%2A> metodę na obiekt w prawidłowy sposób i (gdy używasz go, jak pokazano wcześniej) powoduje <xref:System.IDisposable.Dispose%2A> również, że sam obiekt wykracza poza zakres, jak tylko zostanie wywołana. W `using` obrębie bloku obiekt jest tylko do odczytu i nie można go zmodyfikować ani przypisać ponownie. Jeśli `IAsyncDisposable` obiekt implementuje zamiast `IDisposable`, `using` instrukcja <xref:System.IAsyncDisposable.DisposeAsync%2A> `awaits` wywołuje <xref:System.Threading.Tasks.Task>i zwrócony .

Instrukcja `using` zapewnia, <xref:System.IDisposable.Dispose%2A> że <xref:System.IAsyncDisposable.DisposeAsync%2A>(lub) jest wywoływana, `using` nawet jeśli wystąpi wyjątek w bloku. Ten sam wynik można osiągnąć, umieszczając `try` obiekt wewnątrz <xref:System.IDisposable.Dispose%2A> bloku, a następnie wywołując (lub <xref:System.IAsyncDisposable.DisposeAsync%2A> w `finally` bloku; w rzeczywistości jest to sposób, w jaki `using` instrukcja jest tłumaczona przez kompilator. Przykład kodu wcześniej rozwija się do następującego kodu w czasie kompilacji (zwróć uwagę na dodatkowe nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

Nowsza `using` składnia instrukcji przekłada się na podobny kod. Blok `try` otwiera się, gdy zmienna jest zadeklarowana. Blok `finally` jest dodawany na zamknięciu otaczającego bloku, zazwyczaj na końcu metody.

Aby uzyskać więcej `try` - `finally` informacji na temat instrukcji, zobacz [try-finally](try-finally.md) artykułu.

Wiele wystąpień typu można zadeklarować `using` w pojedynczej instrukcji, jak pokazano w poniższym przykładzie. Należy zauważyć, że nie można używać niejawnie wpisanych zmiennych (`var`) podczas deklarowania wielu zmiennych w jednej instrukcji:

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Można połączyć wiele deklaracji tego samego typu przy użyciu nowej składni wprowadzonej z C# 8, jak pokazano w poniższym przykładzie:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Można utworzyć wystąpienia obiektu zasobu, a następnie `using` przekazać zmienną do instrukcji, ale nie jest to najlepsze rozwiązanie. W takim przypadku po `using` formancie opuszcza blok, obiekt pozostaje w zakresie, ale prawdopodobnie nie ma dostępu do jego zasobów niezarządzanych. Innymi słowy, nie jest już w pełni zainicjowany. Jeśli spróbujesz użyć obiektu `using` poza blokiem, istnieje ryzyko, powodując wyjątek. Z tego powodu lepiej jest utworzyć wystąpienie obiektu `using` w instrukcji i `using` ograniczyć jego zakres do bloku.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Aby uzyskać więcej informacji `IDisposable` na temat usuwania obiektów, zobacz [Używanie obiektów implementujących identyfikator IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [using — Dyrektywa](using-directive.md)
- [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md)
- [Korzystanie z obiektów implementuujalnych IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interfejs IDisposable](xref:System.IDisposable)
- [używanie instrukcji w języku C# 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
