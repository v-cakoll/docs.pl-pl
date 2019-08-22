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
ms.openlocfilehash: 074b97f29946390170abe3c40d71d2ee2cb214ce
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666478"
---
# <a name="using-objects-that-implement-idisposable"></a>Używanie obiektów implementujących interfejs IDisposable

Moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego ponownie przejmuje pamięć używaną przez zarządzane obiekty, ale typy korzystające z zasobów niezarządzanych implementują <xref:System.IDisposable> interfejs, aby umożliwić odzyskanie pamięci przydzielonej do tych niezarządzanych zasobów. Po zakończeniu korzystania z obiektu, który implementuje <xref:System.IDisposable>, należy wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację obiektu. Można to zrobić na jeden z dwóch sposobów:  
  
* C# `Using` Za pomocą instrukcjilub`using` instrukcji Visual Basic.  
  
* Przez implementację `try/finally` bloku.  

## <a name="the-using-statement"></a>Instrukcja using

Instrukcja w C# i`Using` instrukcji w Visual Basic upraszcza kod, który należy napisać, aby utworzyć i oczyścić obiekt. `using` `using` Instrukcja uzyskuje jeden lub więcej zasobów, wykonuje określone instrukcje i automatycznie usuwa obiekt. `using` Jednak instrukcja jest przydatna tylko w przypadku obiektów, które są używane w zakresie metody, w której są zbudowane.  
  
Poniższy przykład używa `using` instrukcji w celu utworzenia i <xref:System.IO.StreamReader?displayProperty=nameWithType> zwolnienia obiektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Należy zauważyć, że <xref:System.IO.StreamReader> mimo że Klasa <xref:System.IDisposable> implementuje interfejs, który wskazuje, że używa niezarządzanego zasobu, <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> przykład nie wywołuje jawnie metody. Gdy kompilator C# lub Visual Basic napotka `using` instrukcję, emituje języka pośredniego (IL), który jest równoważny do poniższego kodu `try/finally` , który jawnie zawiera blok.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Instrukcja umożliwia także uzyskanie wielu zasobów w pojedynczej instrukcji, która jest wewnętrznie odpowiednikiem zagnieżdżonych `using` instrukcji. C# `using` Poniższy przykład tworzy wystąpienie dwóch <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plików.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Blok try/finally

Zamiast zawijać `try/finally` blok `using` w instrukcji, możesz wybrać opcję bezpośredniego wdrożenia `try/finally` bloku. Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:  
  
* Aby dołączyć `catch` blok obsługujący wyjątki zgłoszone `try` w bloku. W przeciwnym razie wszelkie wyjątki zgłoszone `using` przez instrukcję są nieobsługiwane, ponieważ są to wyjątki zgłoszone `using` w bloku, jeśli `try/catch` blok nie jest obecny.  
  
* Aby utworzyć wystąpienie obiektu, który <xref:System.IDisposable> implementuje, którego zakres nie jest lokalny dla bloku, w którym jest zadeklarowany.  
  
Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że `try/catch/finally` używa bloku do tworzenia wystąpienia, używania i usuwania <xref:System.IO.StreamReader> obiektu oraz do obsługi <xref:System.IO.StreamReader> wszelkich wyjątków zgłoszonych przez konstruktora i jego <xref:System.IO.StreamReader.ReadToEnd%2A> metodę. Należy zauważyć, że kod w `finally` bloku sprawdza, czy obiekt, który <xref:System.IDisposable> implementuje `null` , <xref:System.IDisposable.Dispose%2A> nie jest przed wywołaniem metody. Niewykonanie tej czynności może spowodować <xref:System.NullReferenceException> wyjątek w czasie wykonywania.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Możesz użyć tego podstawowego wzorca, jeśli zdecydujesz się zaimplementować lub musi zaimplementować `try/finally` blok, ponieważ język programowania nie `using` obsługuje instrukcji, ale <xref:System.IDisposable.Dispose%2A> zezwala na bezpośrednie wywołania metody. 
  
## <a name="see-also"></a>Zobacz także

- [Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md)
- [using — instrukcjaC# (Reference)](../../csharp/language-reference/keywords/using-statement.md)
- [Using — instrukcja (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
