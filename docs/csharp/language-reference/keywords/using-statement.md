---
title: using — C# odwołanie
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712965"
---
# <a name="using-statement-c-reference"></a>using — instrukcjaC# (Reference)

Zapewnia wygodną składnię, która zapewnia poprawne korzystanie z <xref:System.IDisposable> obiektów.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać instrukcji `using`.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

Począwszy od C# 8,0, można użyć następującej składni alternatywnej dla instrukcji `using`, która nie wymaga nawiasów klamrowych:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Uwagi

<xref:System.IO.File> i <xref:System.Drawing.Font> są przykładami typów zarządzanych, które uzyskują dostęp do niezarządzanych zasobów (w tym przypadku dojścia do plików i konteksty urządzenia). Istnieje wiele innych rodzajów niezarządzanych zasobów i typów bibliotek klas, które hermetyzują. Wszystkie takie typy muszą implementować interfejs <xref:System.IDisposable>.

Gdy okres istnienia obiektu `IDisposable` jest ograniczony do pojedynczej metody, należy zadeklarować ją i utworzyć jej wystąpienie w instrukcji `using`. Instrukcja `using` wywołuje metodę <xref:System.IDisposable.Dispose%2A> na obiekcie w prawidłowy sposób i (gdy jest używana wcześniej), powoduje również, że obiekt nie wyjdzie poza zakres od razu po wywołaniu <xref:System.IDisposable.Dispose%2A>. W bloku `using` obiekt jest tylko do odczytu i nie można go modyfikować ani ponownie przypisywać.

Instrukcja `using` zapewnia, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek w bloku `using`. Można osiągnąć ten sam wynik, umieszczając obiekt wewnątrz bloku `try`, a następnie wywołując <xref:System.IDisposable.Dispose%2A> w bloku `finally`; w rzeczywistości jest to sposób tłumaczenia instrukcji `using` przez kompilator. Przykładowy kod jest rozwinięty do poniższego kodu w czasie kompilacji (należy zwrócić uwagę na dodatkowe nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Nowsza składnia instrukcji `using` Wykonuje translację na bardzo podobny kod. Zostanie otwarty blok `try`, w którym jest zadeklarowana zmienna. Blok `finally` jest dodawany w pobliżu otaczającego bloku, na ogół na końcu metody.

Aby uzyskać więcej informacji na temat instrukcji `try`-`finally`, zobacz temat [try-finally](try-finally.md) .

W instrukcji `using` można zadeklarować wiele wystąpień typu, jak pokazano w następującym przykładzie:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Można połączyć wiele deklaracji tego samego typu, używając nowej składni wprowadzonej przy użyciu C# również 8. Jest to pokazane w poniższym przykładzie:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Można utworzyć wystąpienie obiektu zasobu, a następnie przekazać zmienną do instrukcji `using`, ale nie jest to najlepsze rozwiązanie. W takim przypadku, gdy kontrolka opuszcza blok `using`, obiekt pozostaje w zakresie, ale prawdopodobnie nie ma dostępu do jego niezarządzanych zasobów. Innymi słowy, nie jest już w pełni zainicjowany. Jeśli spróbujesz użyć obiektu poza blokiem `using`, istnieje ryzyko, że zostanie zgłoszony wyjątek. Z tego powodu zwykle lepiej jest utworzyć wystąpienie obiektu w instrukcji `using` i ograniczyć jego zakres do bloku `using`.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Aby uzyskać więcej informacji na temat usuwania obiektów `IDisposable`, zobacz [Używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [instrukcja using](~/_csharplang/spec/statements.md#the-using-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [using, dyrektywa](using-directive.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
- [Używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interfejs IDisposable](xref:System.IDisposable)
- [Instrukcja Using w C# 8,0](~/_csharplang/proposals/csharp-8.0/using.md)
