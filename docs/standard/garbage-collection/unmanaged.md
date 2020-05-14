---
title: Oczyszczanie zasobów niezarządzanych
ms.date: 05/13/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: 2d8b22063a184773928e5bc072f51a9f7d5d45ba
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396990"
---
# <a name="cleaning-up-unmanaged-resources"></a>Oczyszczanie zasobów niezarządzanych

W przypadku większości obiektów tworzonych przez aplikację można polegać na wykorzystaniu [modułu wyrzucania elementów bezużytecznych platformy .NET](index.md) w celu obsługi zarządzania pamięcią. Jednak podczas tworzenia obiektów, które zawierają niezarządzane zasoby, należy jawnie zwolnić te zasoby po zakończeniu korzystania z nich. Najczęściej używane typy zasobów niezarządzanych to obiekty, które zawijają zasoby systemu operacyjnego, takie jak pliki, okna, połączenia sieciowe lub połączenia bazy danych. Mimo że moduł odśmiecania pamięci jest w stanie śledzić okres istnienia obiektu hermetyzującego niezarządzany zasób, nie ma informacji, jak zwolnić i wyczyścić niezarządzany zasób.

Jeśli typy w aplikacji używają niezarządzanych zasobów, należny wykonać następujące czynności:

- Zaimplementuj [wzorzec Dispose](implementing-dispose.md). Wymaga to podania implementacji umożliwiającej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> jednoznaczne wydawanie niezarządzanych zasobów. Odbiorca typu jest wywoływany <xref:System.IDisposable.Dispose%2A> , gdy obiekt (i używane przez niego zasoby) nie są już potrzebne. <xref:System.IDisposable.Dispose%2A>Metoda natychmiast zwalnia niezarządzane zasoby.

- W przypadku, gdy odbiorca typu zapomni o wywołaniu <xref:System.IDisposable.Dispose%2A> , Zapewnij możliwość zwolnienia niezarządzanych zasobów. Istnieją dwa sposoby wykonania tej czynności:

  - Użycie bezpiecznego dojścia w celu umieszczenie niezarządzanego zasobu w otoce. Jest to zalecana technika. Bezpieczne dojścia są uzyskiwane z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy abstrakcyjnej i zawierają niezawodną <xref:System.Object.Finalize%2A> metodę. W przypadku używania bezpiecznego dojścia, wystarczy zaimplementować <xref:System.IDisposable> interfejs i wywołać metodę bezpiecznego dojścia <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> w <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. Finalizator bezpiecznego dojścia jest automatycznie wywoływany przez moduł wyrzucania elementów bezużytecznych, jeśli jego <xref:System.IDisposable.Dispose%2A> Metoda nie jest wywoływana.

    —**lub**—

  - Zastąp <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodę. Finalizowanie umożliwia niedeterministyczną wydawanie niezarządzanych zasobów, gdy odbiorca typu nie może wywoływać metody <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Dispose w sposób niejednoznaczny. Zdefiniuj [finalizator](../../csharp/programming-guide/classes-and-structs/destructors.md) , zastępując <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodę.

  > [!WARNING]
  > Jednak ponieważ finalizowanie obiektów może być złożoną i podatną na błędy, zalecamy użycie bezpiecznego uchwytu zamiast podawania własnych finalizatorów.

Odbiorcy typu mogą następnie wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację bezpośrednio do wolnej pamięci używanej przez niezarządzane zasoby. Po poprawnym zaimplementowaniu <xref:System.IDisposable.Dispose%2A> metody, Metoda bezpiecznego dojścia <xref:System.Object.Finalize%2A> lub własne przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody staną się zabezpieczeniem w celu oczyszczenia zasobów w przypadku, gdy <xref:System.IDisposable.Dispose%2A> Metoda nie jest wywoływana.

## <a name="in-this-section"></a>W tej sekcji

[Implementacja metody Dispose](implementing-dispose.md) opisuje sposób implementacji wzorca Dispose do zwalniania niezarządzanych zasobów.

[Używanie obiektów implementujących `IDisposable` ](../../../docs/standard/garbage-collection/using-objects.md) Opisuje, jak konsumenci typu zapewniają, że jego <xref:System.IDisposable.Dispose%2A> implementacja jest wywoływana. Zalecamy użycie w `using` tym celu instrukcji języka C# (lub Visual Basic `Using` ).

## <a name="reference"></a>Dokumentacja

| Typ/element członkowski | Opis |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | Definiuje <xref:System.IDisposable.Dispose%2A> metodę zwalniania niezarządzanych zasobów. |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | Zapewnia finalizowanie obiektów, jeśli niezarządzane zasoby nie są uwalniane przez <xref:System.IDisposable.Dispose%2A> metodę. |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | Pomija finalizację. Ta metoda jest zwykle wywoływana z `Dispose` metody, aby zapobiec wykonywaniu finalizatorów. |
