---
title: Używanie obiektów implementujących interfejs IDisposable
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25c5ffa89e6ce4e589b8f12a7b8518272426c9e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969497"
---
# <a name="using-objects-that-implement-idisposable"></a>Używanie obiektów implementujących interfejs IDisposable

Moduł wyrzucania elementów bezużytecznych wykonywalnych języka wspólnego odzyskuje pamięć używaną przez zarządzane obiekty, ale typy używające niezarządzanych zasobów implementują <xref:System.IDisposable> interfejsu, aby umożliwić pamięci przydzielonych do tych niezarządzanych zasobów, które można odzyskać. Po zakończeniu używania obiektu, który implementuje <xref:System.IDisposable>, należy wywołać obiektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. Można to zrobić na jeden z dwóch sposobów:  
  
* Za pomocą języka C# `using` instrukcji lub Visual Basic `Using` instrukcji.  
  
* Implementując `try/finally` bloku.  

## <a name="the-using-statement"></a>Instrukcja using

`using` Instrukcji w języku C# i `Using` instrukcji w języku Visual Basic upraszczają kod, który trzeba napisać, aby utworzyć i oczyścić obiekt. `using` Instrukcji uzyskuje co najmniej jeden zasób, wykonuje instrukcje określone przez użytkownika, a następnie automatycznie usuwa obiekt. Jednak `using` instrukcja jest użyteczna tylko w przypadku obiektów używanych zakresie metody, w której zostały skonstruowane.  
  
W poniższym przykładzie użyto `using` instrukcję w celu utworzenia i zwolnienia <xref:System.IO.StreamReader?displayProperty=nameWithType> obiektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Należy pamiętać, że chociaż <xref:System.IO.StreamReader> klasy implementuje <xref:System.IDisposable> interfejs, który wskazuje, że używa niezarządzany zasób, nie jest jawnie wywoływana przykład <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody. Gdy kompilator języka C# lub Visual Basic napotyka `using` instrukcji, emituje języka pośredniego (IL), który jest odpowiednikiem następujący kod, który jawnie zawiera `try/finally` bloku.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` instrukcji umożliwia również nabywanie wielu zasobów w pojedynczej instrukcji, co stanowi wewnętrzny odpowiednik zagnieżdżonych `using` instrukcji. Poniższy przykład tworzy dwie <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plikach.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Blok try/finally

Zamiast umieszczać `try/finally` bloku `using` instrukcji może zadecydować o stosowaniu `try/finally` zablokować bezpośrednio. Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:  
  
* Aby uwzględnić `catch` bloku w celu obsługi wszystkich wyjątków zgłaszanych `try` bloku. W przeciwnym razie wyjątki zgłaszane przez `using` instrukcji są obsługiwane, podobnie jak wyjątki zgłaszane w `using` zablokować, jeśli `try/catch` blok nie jest obecny.  
  
* Aby utworzyć wystąpienie obiektu, który implementuje <xref:System.IDisposable> którego zakres nie jest lokalnym bloku, w którym jest zdeklarowana.  
  
Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa `try/catch/finally` bloku, aby utworzyć wystąpienie, używanie i usuwanie <xref:System.IO.StreamReader> obiekt oraz do obsługi wszystkich wyjątków zgłaszanych przez <xref:System.IO.StreamReader> Konstruktor i jego <xref:System.IO.StreamReader.ReadToEnd%2A> metody. Należy pamiętać, że kod w `finally` bloku sprawdza, czy obiekt implementujący <xref:System.IDisposable> nie jest `null` przed wywołaniem <xref:System.IDisposable.Dispose%2A> metody. Niewykonanie tej czynności to może spowodować <xref:System.NullReferenceException> wyjątek w czasie wykonywania.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Możesz wykonać tego podstawowego wzorca, jeśli zadecydować o stosowaniu lub musi implementować `try/finally` zablokować, ponieważ nie obsługuje języka programowania `using` instrukcji, ale zezwala na bezpośrednie wywołania do <xref:System.IDisposable.Dispose%2A> metody. 
  
## <a name="see-also"></a>Zobacz także

- [Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md)
- [Using — instrukcja (odwołanie w C#)](~/docs/csharp/language-reference/keywords/using-statement.md)
- [Using — instrukcja (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
