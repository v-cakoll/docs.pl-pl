---
title: "Używanie obiektów implementujących interfejs IDisposable"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a>Używanie obiektów implementujących interfejs IDisposable

Środowisko uruchomieniowe języka wspólnego przez moduł Garbage Collector zwraca pamięć używana przez obiekty zarządzane, ale implementuje typów, które używają zasoby niezarządzane <xref:System.IDisposable> interfejs umożliwia pamięć przydzielona do tych zasobów niezarządzanych. można odzyskać. Po zakończeniu przy użyciu obiektu implementującego <xref:System.IDisposable>, należy wywołać obiektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. Można to zrobić na jeden z dwóch sposobów:  
  
* Z języka C# `using` instrukcji lub Visual Basic `Using` instrukcji.  
  
* Zaimplementowanie `try/finally` bloku.  

## <a name="the-using-statement"></a>Instrukcja using

`using` Instrukcji w języku C# i `Using` instrukcji w języku Visual Basic uprościć kod, który musi być zapisana do tworzenia i wyczyścić obiektu. `using` Instrukcji uzyskuje jeden lub więcej zasobów, wykonuje instrukcje, które określają i automatycznie usuwa obiektu. Jednak `using` instrukcji przydaje się tylko dla obiektów, które są używane w zakresie metody, w których są wykonane.  
  
W poniższym przykładzie użyto `using` instrukcji, aby utworzyć i zwolnij <xref:System.IO.StreamReader?displayProperty=nameWithType> obiektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Należy pamiętać, że chociaż <xref:System.IO.StreamReader> klasa implementuje <xref:System.IDisposable> interfejs, który wskazuje, że używa niezarządzanym zasobem przykładzie nie jawnie wywołać <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody. Gdy wystąpi kompilatora C# lub Visual Basic `using` instrukcji, emituje język pośredni (IL), który jest odpowiednikiem następujący kod, który zawiera jawnie `try/finally` bloku.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` instrukcji pozwala również uzyskać wiele zasobów w jednej instrukcji, który jest odpowiednikiem wewnętrznie zagnieżdżone `using` instrukcje. Poniższy przykład tworzy dwa <xref:System.IO.StreamReader> obiekty do odczytu treści dwóch różnych plików.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Blok try/finally

Zamiast zawijania `try/finally` blok w `using` instrukcji, może zadecydować o stosowaniu `try/finally` zablokować bezpośrednio. Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:  
  
* Aby uwzględnić `catch` bloku do obsługi wszelkie wyjątki zgłaszane `try` bloku. W przeciwnym razie wartość, wszelkie wyjątki zgłaszane przez `using` instrukcji są nieobsługiwany, ponieważ są wszelkie wyjątki zgłaszane w `using` zablokować, jeśli `try/catch` bloku nie jest obecny.  
  
* Można utworzyć wystąpienia obiektu implementującego <xref:System.IDisposable> którego zakres nie jest lokalny blok, w którym jest zadeklarowany.  
  
Poniższy przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że używa `try/catch/finally` blok do tworzenia wystąpienia, używanie i usuwanie <xref:System.IO.StreamReader> obiektu i do obsługi wszelkie wyjątki zgłaszane przez <xref:System.IO.StreamReader> Konstruktor i jego <xref:System.IO.StreamReader.ReadToEnd%2A> — metoda. Należy pamiętać, że kod w `finally` bloku sprawdza, czy obiekt z zaimplementowanym interfejsem <xref:System.IDisposable> nie jest `null` przed wywołaniem <xref:System.IDisposable.Dispose%2A> metody. Może spowodować niepowodzenie w tym celu <xref:System.NullReferenceException> wyjątek w czasie wykonywania.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Możesz wykonać ten podstawowy wzorzec zadecydować o stosowaniu lub musi implementować `try/finally` zablokować, ponieważ nie obsługuje języka programowania `using` instrukcji, ale zezwala na bezpośrednie wywołania <xref:System.IDisposable.Dispose%2A> metody. 
  
## <a name="see-also"></a>Zobacz także

[Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md)   
[Using — instrukcja (odwołanie w C#)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[Using — instrukcja (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
