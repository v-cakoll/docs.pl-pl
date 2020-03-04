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
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160287"
---
# <a name="using-objects-that-implement-idisposable"></a>Używanie obiektów implementujących interfejs IDisposable

Moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego języka wspólnego nie przejmuje pamięci używanej przez zarządzane obiekty, ale typy korzystające z zasobów niezarządzanych implementują interfejs <xref:System.IDisposable>, aby umożliwić odzyskanie pamięci przydzielonej do tych niezarządzanych zasobów. Po zakończeniu korzystania z obiektu, który implementuje <xref:System.IDisposable>, należy wywołać implementację <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> obiektu. Można to zrobić na jeden z dwóch sposobów:  
  
- Za pomocą C# instrukcji `using` lub instrukcji Visual Basic `Using`.  
  
- Implementując blok `try/finally`.  

## <a name="the-using-statement"></a>Instrukcja using

Instrukcja `using` w C# i instrukcji `Using` w Visual Basic upraszcza kod, który należy napisać, aby utworzyć i oczyścić obiekt. Instrukcja `using` uzyskuje jeden lub więcej zasobów, wykonuje określone instrukcje i automatycznie usuwa obiekt. Jednakże instrukcja `using` jest przydatna tylko w przypadku obiektów, które są używane w zakresie metody, w której są zbudowane.  
  
Poniższy przykład używa instrukcji `using` w celu utworzenia i zwolnienia obiektu <xref:System.IO.StreamReader?displayProperty=nameWithType>.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Należy zauważyć, że chociaż Klasa <xref:System.IO.StreamReader> implementuje interfejs <xref:System.IDisposable>, co oznacza, że używa niezarządzanego zasobu, przykład nie wywołuje jawnie metody <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>. Gdy kompilator C# lub Visual Basic napotka instrukcję `using`, emituje języka pośredniego (IL), który jest odpowiednikiem poniższego kodu, który jawnie zawiera blok `try/finally`.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Instrukcja C# `using` umożliwia także uzyskanie wielu zasobów w pojedynczej instrukcji, która jest wewnętrznie odpowiednikiem zagnieżdżonych instrukcji `using`. Poniższy przykład tworzy wystąpienie dwóch <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plików.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Blok try/finally

Zamiast zawijać blok `try/finally` w instrukcji `using`, można wybrać opcję bezpośredniego wdrożenia bloku `try/finally`. Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:  
  
- Aby dołączyć blok `catch` do obsługi wyjątków zgłoszonych w bloku `try`. W przeciwnym razie wszelkie wyjątki zgłoszone przez instrukcję `using` są nieobsługiwane, ponieważ są to wyjątki zgłoszone w bloku `using`, jeśli blok `try/catch` nie jest obecny.  
  
- Aby utworzyć wystąpienie obiektu, który implementuje <xref:System.IDisposable> którego zakres nie jest lokalny dla bloku, w którym jest zadeklarowany.  
  
Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa bloku `try/catch/finally` do tworzenia wystąpienia, używania i usuwania obiektu <xref:System.IO.StreamReader> oraz do obsługi wyjątków zgłoszonych przez konstruktora <xref:System.IO.StreamReader> i jego metody <xref:System.IO.StreamReader.ReadToEnd%2A>. Należy zauważyć, że kod w bloku `finally` sprawdza, czy obiekt implementujący <xref:System.IDisposable> nie jest `null` przed wywołaniem metody <xref:System.IDisposable.Dispose%2A>. Niewykonanie tej czynności może spowodować <xref:System.NullReferenceException> wyjątek w czasie wykonywania.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Ten podstawowy wzorzec można wykonać, jeśli zdecydujesz się zaimplementować lub zaimplementować blok `try/finally`, ponieważ język programowania nie obsługuje instrukcji `using`, ale zezwala na bezpośrednie wywołania metody <xref:System.IDisposable.Dispose%2A>.
  
## <a name="see-also"></a>Zobacz też

- [Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md)
- [using — instrukcjaC# (Reference)](../../csharp/language-reference/keywords/using-statement.md)
- [Using — instrukcja (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
