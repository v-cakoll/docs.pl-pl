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
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423039"
---
# <a name="cleaning-up-unmanaged-resources"></a>Oczyszczanie zasobów niezarządzanych

W przypadku większości obiektów tworzonych przez aplikację można polegać na. Moduł wyrzucania elementów bezużytecznych sieci do obsługi zarządzania pamięcią. Jeśli jednak są tworzone obiekty zawierające niezarządzane zasoby, należy jawnie zwalniać te zasoby po zakończeniu używania ich w aplikacji. Najpopularniejsze typy niezarządzanych zasobów to obiekty, które umieszczają w otoce zasoby systemu operacyjnego, takie jak pliki, okna, połączenia sieciowe lub połączenia bazy danych. Mimo że moduł odśmiecania pamięci jest w stanie śledzić okres istnienia obiektu hermetyzującego niezarządzany zasób, nie ma informacji, jak zwolnić i wyczyścić niezarządzany zasób.

Jeśli typy w aplikacji używają niezarządzanych zasobów, należny wykonać następujące czynności:

- Zaimplementuj [wzorzec Dispose](implementing-dispose.md). Wymaga to podania implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, aby umożliwić deterministyczne wydawanie niezarządzanych zasobów. Odbiorca typu wywołuje <xref:System.IDisposable.Dispose%2A>, gdy obiekt (i używane przez niego zasoby) nie jest już wymagany. Metoda <xref:System.IDisposable.Dispose%2A> natychmiast zwalnia niezarządzane zasoby.

- Określ, że niezarządzane zasoby mają zostać wydane w przypadku, gdy konsument typu zapomni, aby wywoływać <xref:System.IDisposable.Dispose%2A>. Istnieją dwa sposoby wykonania tej czynności:

  - Użycie bezpiecznego dojścia w celu umieszczenie niezarządzanego zasobu w otoce. Jest to zalecana technika. Bezpieczne dojścia są uzyskiwane z klasy <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> i zawierają niezawodną metodę <xref:System.Object.Finalize%2A>. W przypadku używania bezpiecznego dojścia należy po prostu zaimplementować interfejs <xref:System.IDisposable> i wywołać metodę <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> bezpiecznego dojścia w <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. Finalizator bezpiecznego dojścia jest automatycznie wywoływany przez moduł wyrzucania elementów bezużytecznych, jeśli nie zostanie wywołana jego Metoda <xref:System.IDisposable.Dispose%2A>.

    —lub—

  - Zastąp metodę <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Finalizowanie umożliwia niedeterministyczną wydawanie niezarządzanych zasobów, gdy odbiorca typu nie może wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, aby usunąć z nich deterministycznie. Jednak finalizacja obiektu może być złożoną i podatną na błędy operacją, więc zalecane jest używanie bezpiecznego dojścia, zamiast dostarczania własnego finalizatora.

Odbiorcy typu mogą następnie wywoływać implementację <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bezpośrednio, aby zwolnić pamięć używaną przez niezarządzane zasoby. Po poprawnym zaimplementowaniu metody <xref:System.IDisposable.Dispose%2A>, Metoda <xref:System.Object.Finalize%2A> bezpiecznego dojścia lub własne przesłonięcie metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType>j będzie zabezpieczeniem czyszczenia zasobów w przypadku, gdy metoda <xref:System.IDisposable.Dispose%2A> nie zostanie wywołana.

## <a name="in-this-section"></a>W tej sekcji

[Implementowanie metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md) Opisuje sposób implementacji [wzorca Dispose](implementing-dispose.md) do zwalniania niezarządzanych zasobów.

[Używanie obiektów implementujących interfejs IDisposable](../../../docs/standard/garbage-collection/using-objects.md) Opisuje, jak konsumenci typu zapewniają, że jego implementacja <xref:System.IDisposable.Dispose%2A> jest wywoływana. Zalecamy użycie instrukcji C# `using` lub instrukcji Visual Basic `Using`.

## <a name="reference"></a>Tematy pomocy

<xref:System.IDisposable?displayProperty=nameWithType>\
Definiuje metodę <xref:System.IDisposable.Dispose%2A> do zwalniania niezarządzanych zasobów.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Zapewnia finalizowanie obiektów, jeśli niezarządzane zasoby nie są uwalniane przez metodę <xref:System.IDisposable.Dispose%2A>.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Pomija finalizację. Ta metoda jest zwykle wywoływana z metody `Dispose`, aby zapobiec wykonywaniu finalizatorów.
