---
title: Korzystanie z obiektów implementujących IDisposable
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160287"
---
# <a name="using-objects-that-implement-idisposable"></a>Korzystanie z obiektów implementujących IDisposable

Moduł zbierający elementy bezużyteczne w czasie wykonywania języka wspólnego odzyskuje pamięć używaną <xref:System.IDisposable> przez obiekty zarządzane, ale typy korzystające z zasobów niezarządzanych implementują interfejs, aby umożliwić odzyskanie pamięci przydzielonej do tych niezarządzanych zasobów. Po zakończeniu przy użyciu obiektu, który implementuje <xref:System.IDisposable>, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> należy wywołać implementacji obiektu. Można to zrobić na jeden z dwóch sposobów:  
  
- Z C# `using` instrukcji lub `Using` Visual Basic instrukcji.  
  
- Implementując `try/finally` blok.  

## <a name="the-using-statement"></a>Instrukcja using

Instrukcja `using` w języku `Using` C# i instrukcji w języku Visual Basic uprościć kod, który należy napisać, aby utworzyć i oczyścić obiekt. Instrukcja `using` uzyskuje jeden lub więcej zasobów, wykonuje instrukcje, które określisz i automatycznie usuwa obiekt. Jednak instrukcja `using` jest przydatna tylko dla obiektów, które są używane w zakresie metody, w którym są one konstruowane.  
  
W poniższym `using` przykładzie użyto instrukcji <xref:System.IO.StreamReader?displayProperty=nameWithType> do utworzenia i zwolnienia obiektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Należy zauważyć, <xref:System.IO.StreamReader> że mimo <xref:System.IDisposable> że klasa implementuje interfejs, co wskazuje, że używa zasobu niezarządzanego, w przykładzie nie jawnie wywołać <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metodę. Gdy kompilator Języka C# `using` lub Visual Basic napotka instrukcję, emituje język pośredni (IL), `try/finally` który jest odpowiednikiem następującego kodu, który jawnie zawiera blok.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Instrukcja `using` C# umożliwia również uzyskanie wielu zasobów w jednej instrukcji, która `using` jest wewnętrznie równoważna zagnieżdżonych instrukcji. Poniższy przykład tworzy dwa <xref:System.IO.StreamReader> obiekty do odczytu zawartości dwóch różnych plików.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Blok try/finally

Zamiast zawijania `try/finally` bloku w `using` instrukcji, `try/finally` można zaimplementować blok bezpośrednio. Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:  
  
- Aby dołączyć `catch` blok do obsługi wyjątków `try` zgłoszonych w bloku. W przeciwnym razie wszelkie `using` wyjątki generowane przez instrukcję są nieobsługiwane, podobnie jak wszelkie wyjątki generowane w `using` bloku, jeśli `try/catch` blok nie jest obecny.  
  
- Aby utworzyć wystąpienia obiektu, który <xref:System.IDisposable> implementuje którego zakres nie jest lokalny do bloku, w którym jest zadeklarowany.  
  
Poniższy przykład jest podobny do poprzedniego przykładu, `try/catch/finally` z tą różnicą, że używa <xref:System.IO.StreamReader> bloku do tworzenia wystąpienia, używania <xref:System.IO.StreamReader> i usuwania <xref:System.IO.StreamReader.ReadToEnd%2A> obiektu oraz do obsługi wszelkich wyjątków zgłaszanych przez konstruktora i jego metodę. Należy zauważyć, że `finally` kod w bloku sprawdza, czy `null` obiekt, <xref:System.IDisposable.Dispose%2A> który implementuje <xref:System.IDisposable> nie jest przed wywołaniem metody. Niezastosowanie się do tego <xref:System.NullReferenceException> może spowodować wyjątek w czasie wykonywania.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Można wykonać ten podstawowy wzorzec, jeśli `try/finally` zdecydujesz się zaimplementować lub musi `using` zaimplementować blok, <xref:System.IDisposable.Dispose%2A> ponieważ język programowania nie obsługuje instrukcji, ale zezwala na bezpośrednie wywołania metody.
  
## <a name="see-also"></a>Zobacz też

- [Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md)
- [using — Instrukcja (odwołanie w C#)](../../csharp/language-reference/keywords/using-statement.md)
- [Using — Instrukcja (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
