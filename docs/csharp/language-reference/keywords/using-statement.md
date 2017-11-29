---
title: "using — Instrukcja (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a>using — Instrukcja (odwołanie w C#)
Umożliwia wygodne składnię, która zapewnia prawidłowe użycie <xref:System.IDisposable> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie przy użyciu instrukcji.  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.IO.File>i <xref:System.Drawing.Font> przedstawiono przykładowe typy zarządzane, które uzyskują dostęp do zasobów niezarządzanych (w tym dojścia do plików w przypadku i konteksty urządzenia). Istnieje wiele rodzajów zasoby niezarządzane i klasy biblioteki typów, które hermetyzują je. Takich typów musi implementować <xref:System.IDisposable> interfejsu.  
  
Jeśli okres istnienia `IDisposable` obiektu jest ograniczony do pojedynczej metody, należy zadeklarować i utworzyć w `using` instrukcji. `using` Wywołania instrukcji <xref:System.IDisposable.Dispose%2A> metody dla obiekt w prawidłowy sposób i (gdy jest używany jak pokazano wcześniej) powoduje także obiekt, aby znaleźć poza zakresem natychmiast <xref:System.IDisposable.Dispose%2A> jest wywoływana. W ramach `using` bloku, obiekt jest tylko do odczytu i nie można zmodyfikować lub ponownie przypisany.  
  
 `using` Instrukcji upewnia się, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek podczas wywoływania metody dla obiektu. Umieszczanie obiektu wewnątrz bloku try, a następnie podczas wywoływania można osiągnąć ten sam rezultat <xref:System.IDisposable.Dispose%2A> w bloku finally; w rzeczywistości jest to sposób `using` instrukcji jest przetłumaczony przez kompilator. Przykładowy kod wcześniej rozwijany do następującego kodu w czasie kompilacji (Uwaga: dodatkowe nawiasy klamrowe do utworzenia ograniczony zakres dla obiekt):  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 Wiele wystąpień tego typu mogą być deklarowane w `using` instrukcji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Można utworzyć wystąpienia obiektu zasobów, a następnie przekazać zmiennej `using` instrukcji, ale nie jest najlepszym rozwiązaniem. W takim przypadku obiekt pozostaje w zakresie po sterowanie wyjdzie `using` zablokować, mimo że prawdopodobnie nie ma dostępu do jego zasoby niezarządzane. Innymi słowy jego będzie już można w pełni zainicjowany. Jeśli spróbujesz użyć obiektu poza `using` zablokować ryzyka powoduje wyjątków. Z tego powodu najlepiej ogólnie można utworzyć wystąpienia obiektu w `using` instrukcji i ograniczyć zakres do `using` bloku.  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
Aby uzyskać więcej informacji na temat usuwania `IDisposable` obiekty, zobacz [przy użyciu obiektów, które implementują interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Using — Dyrektywa](../../../csharp/language-reference/keywords/using-directive.md)  
 [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md)  
 [Używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md)  
 [Interfejs IDisposable](xref:System.IDisposable)
