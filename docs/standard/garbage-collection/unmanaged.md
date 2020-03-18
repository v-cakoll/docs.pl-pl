---
title: Oczyszczanie zasobów niezarządzanych
ms.date: 03/30/2017
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
ms.openlocfilehash: e05cfb949ee3f206f212ca7015f3ff4c22cd2a12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423039"
---
# <a name="cleaning-up-unmanaged-resources"></a>Oczyszczanie zasobów niezarządzanych

Dla większości obiektów, które tworzy aplikacja, można polegać na . Moduł odśmiecania pamięci net do obsługi zarządzania pamięcią. Jeśli jednak są tworzone obiekty zawierające niezarządzane zasoby, należy jawnie zwalniać te zasoby po zakończeniu używania ich w aplikacji. Najpopularniejsze typy niezarządzanych zasobów to obiekty, które umieszczają w otoce zasoby systemu operacyjnego, takie jak pliki, okna, połączenia sieciowe lub połączenia bazy danych. Mimo że moduł odśmiecania pamięci jest w stanie śledzić okres istnienia obiektu hermetyzującego niezarządzany zasób, nie ma informacji, jak zwolnić i wyczyścić niezarządzany zasób.

Jeśli typy w aplikacji używają niezarządzanych zasobów, należny wykonać następujące czynności:

- Zaimplementuj [wzorzec usuwania](implementing-dispose.md). Wymaga to podania <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji w celu umożliwienia deterministycznego uwolnienia zasobów niezarządzanych. Konsument typu wywołuje, <xref:System.IDisposable.Dispose%2A> gdy obiekt (i zasoby, które używa) nie jest już potrzebne. Metoda <xref:System.IDisposable.Dispose%2A> natychmiast zwalnia zasoby niezarządzane.

- Zapewnij, aby zasoby niezarządzane zostały zwolnione w przypadku, gdy <xref:System.IDisposable.Dispose%2A>konsument tego typu zapomni zadzwonić. Istnieją dwa sposoby wykonania tej czynności:

  - Użycie bezpiecznego dojścia w celu umieszczenie niezarządzanego zasobu w otoce. Jest to zalecana technika. Bezpieczne uchwyty są uzyskiwane z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy <xref:System.Object.Finalize%2A> i zawierają niezawodną metodę. Korzystając z bezpiecznego dojścia, wystarczy zaimplementować <xref:System.IDisposable> <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> interfejs i <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> wywołać metodę bezpiecznego dojścia w implementacji. Finalizator bezpiecznego dojścia jest wywoływany automatycznie <xref:System.IDisposable.Dispose%2A> przez moduł zbierający elementy bezużyteczne, jeśli jego metoda nie jest wywoływana.

    —lub—

  - Zastąp <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodę. Finalizacja umożliwia niedeterministyczne uwolnienie zasobów niezarządzanych, gdy konsument <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> typu nie może wywołać ich usuwania deterministycznie. Jednak finalizacja obiektu może być złożoną i podatną na błędy operacją, więc zalecane jest używanie bezpiecznego dojścia, zamiast dostarczania własnego finalizatora.

Konsumenci tego typu mogą <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> następnie wywołać implementację bezpośrednio do wolnej pamięci używanej przez zasoby niezarządzane. Po prawidłowym <xref:System.IDisposable.Dispose%2A> zaimplementować metodę, metoda <xref:System.Object.Finalize%2A> bezpiecznego dojścia <xref:System.Object.Finalize%2A?displayProperty=nameWithType> lub własne zastąpienie metody staje się zabezpieczeniem, aby oczyścić zasoby w przypadku, gdy <xref:System.IDisposable.Dispose%2A> metoda nie jest wywoływana.

## <a name="in-this-section"></a>W tej sekcji

[Implementowanie metody utylizacji](../../../docs/standard/garbage-collection/implementing-dispose.md) W tym artykule opisano sposób implementowania [wzorca usuwania](implementing-dispose.md) do zwalniania zasobów niezarządzanych.

[Korzystanie z obiektów, które implementują idisposable](../../../docs/standard/garbage-collection/using-objects.md) Opisuje, jak konsumenci typu <xref:System.IDisposable.Dispose%2A> upewnij się, że jego implementacja jest wywoływana. W tym celu `using` zaleca się użycie `Using` instrukcji Języka C# lub instrukcji Języka Visual Basic.

## <a name="reference"></a>Dokumentacja

<xref:System.IDisposable?displayProperty=nameWithType>\
Definiuje <xref:System.IDisposable.Dispose%2A> metodę zwalniania zasobów niezarządzanych.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Przewiduje finalizację obiektu, jeśli niezarządzane <xref:System.IDisposable.Dispose%2A> zasoby nie są zwalniane przez metodę.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Pomija finalizację. Ta metoda jest zwyczajowo `Dispose` wywoływana z metody, aby zapobiec finalizator z wykonywania.
