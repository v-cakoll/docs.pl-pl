---
title: Obsługa wyjątków — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: ee1e5bd15183dad9ffe97824f9b194668e9d3b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705304"
---
# <a name="exception-handling-c-programming-guide"></a>Obsługa wyjątków (Przewodnik programowania w języku C#)
Blok [try](../../language-reference/keywords/try-catch.md) jest używany przez programistów Języka C# do partycji kodu, który może mieć wpływ na wyjątek. Skojarzone bloki [catch](../../language-reference/keywords/try-catch.md) są używane do obsługi wszelkich wyjątków wynikowych. Finally [finally](../../language-reference/keywords/try-finally.md) bloku zawiera kod, który jest uruchamiany niezależnie od `try` tego, czy wyjątek jest zgłaszany `try` w bloku, takich jak zwalnianie zasobów, które są przydzielane w bloku. Blok `try` wymaga jednego lub `catch` więcej skojarzonych bloków lub `finally` bloku lub obu.  
  
 W poniższych przykładach przedstawiono `try-finally` instrukcję, `try-catch-finally` `try-catch` instrukcję i instrukcję.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Blok `try` bez `catch` lub `finally` bloku powoduje błąd kompilatora.  
  
## <a name="catch-blocks"></a>Złap bloki  
 Blok `catch` można określić typ wyjątku do połowu. Specyfikacja typu jest nazywana *filtrem wyjątków*. Typ wyjątku powinien pochodzić od <xref:System.Exception>. Ogólnie rzecz biorąc <xref:System.Exception> nie należy określać jako filtr wyjątku, chyba że wiesz, `try` jak obsługiwać wszystkie wyjątki, które mogą `catch` być generowane w bloku lub zostały uwzględnione [throw](../../language-reference/keywords/throw.md) instrukcji na końcu bloku.  
  
 Wiele `catch` bloków z różnymi filtrami wyjątków można połączyć ze sobą. Bloki `catch` są oceniane od góry do dołu w `catch` kodzie, ale tylko jeden blok jest wykonywany dla każdego wyjątku, który jest generowany. Pierwszy `catch` blok, który określa dokładny typ lub klasy podstawowej wyjątek jest wykonywana. Jeśli `catch` żaden blok nie określa pasującego filtru `catch` wyjątków, wybrany jest blok, który nie ma filtra, jeśli jest obecny w instrukcji. Ważne jest, `catch` aby najpierw umieścić bloki z najbardziej szczegółowymi (czyli najbardziej pochodnymi) typami wyjątków.  
  
 Należy przechwycić wyjątki, gdy spełnione są następujące warunki:  
  
- Masz dobre zrozumienie, dlaczego wyjątek może być generowany i można zaimplementować określonego odzyskiwania, takich jak monitowanie użytkownika, aby wprowadzić nową nazwę pliku podczas połowu <xref:System.IO.FileNotFoundException> obiektu.  
  
- Można utworzyć i zgłosić nowy, bardziej szczegółowy wyjątek.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcesz częściowo obsługiwać wyjątek przed przekazaniem go do dodatkowej obsługi. W poniższym `catch` przykładzie blok służy do dodawania wpisu do dziennika błędów przed ponownym zgłoszeniem wyjątku.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Wreszcie bloki  
 Blok `finally` umożliwia oczyszczanie akcji wykonywanych w `try` bloku. Jeśli jest `finally` obecny, blok wykonuje `try` ostatni, po `catch` bloku i wszelkie dopasowane bloku. Blok `finally` zawsze działa, niezależnie od tego, czy `catch` wyjątek lub blok pasujący do typu wyjątku zostanie znaleziony.  
  
 Blok `finally` może służyć do zwalniania zasobów, takich jak strumienie plików, połączenia bazy danych i uchwyty grafiki bez oczekiwania na moduł zbierający elementy bezużyteczne w czasie wykonywania, aby sfinalizować obiekty. Aby uzyskać więcej [informacji, zobacz korzystanie z instrukcji.](../../language-reference/keywords/using-statement.md)  
  
 W poniższym `finally` przykładzie blok służy do zamykania pliku, `try` który jest otwarty w bloku. Należy zauważyć, że stan dojścia do plików jest sprawdzany przed zamknięciem pliku. Jeśli `try` blok nie może otworzyć pliku, dojście do pliku nadal ma wartość, `null` a `finally` blok nie próbuje go zamknąć. Alternatywnie, jeśli plik zostanie pomyślnie `try` otwarty w `finally` bloku, blok zamyka otwarty plik.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) and [The try statement](~/_csharplang/spec/statements.md#the-try-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [za pomocą instrukcji](../../language-reference/keywords/using-statement.md)
