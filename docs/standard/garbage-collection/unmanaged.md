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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e32d2d4424d05b95af1eda400974da3293b8499
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969107"
---
# <a name="cleaning-up-unmanaged-resources"></a>Oczyszczanie zasobów niezarządzanych
Dla większości obiektów tworzonych przez aplikację na których możesz polegać. Moduł wyrzucania elementów bezużytecznych przez sieć do obsługi zarządzania pamięcią. Jeśli jednak są tworzone obiekty zawierające niezarządzane zasoby, należy jawnie zwalniać te zasoby po zakończeniu używania ich w aplikacji. Najpopularniejsze typy niezarządzanych zasobów to obiekty, które umieszczają w otoce zasoby systemu operacyjnego, takie jak pliki, okna, połączenia sieciowe lub połączenia bazy danych. Mimo że moduł odśmiecania pamięci jest w stanie śledzić okres istnienia obiektu hermetyzującego niezarządzany zasób, nie ma informacji, jak zwolnić i wyczyścić niezarządzany zasób.  
  
 Jeśli typy w aplikacji używają niezarządzanych zasobów, należny wykonać następujące czynności:  
  
- Implementowanie [wzorca usuwania](../../../docs/standard/design-guidelines/dispose-pattern.md). Wymaga to, że podajesz <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji w celu umożliwienia deterministycznego zwalniania niezarządzanych zasobów. Konsument typu wywołuje metodę <xref:System.IDisposable.Dispose%2A> kiedy obiekt (i przez niego zasoby) nie jest już potrzebny. <xref:System.IDisposable.Dispose%2A> Metoda natychmiast zwalnia niezarządzane zasoby.  
  
- Obejmij swoje zasoby niezarządzane, mogą być wprowadzane w przypadku, gdy konsument typu zapomni wywołać <xref:System.IDisposable.Dispose%2A>. Istnieją dwa sposoby wykonania tej czynności:  
  
    - Użycie bezpiecznego dojścia w celu umieszczenie niezarządzanego zasobu w otoce. Jest to zalecana technika. Bezpieczne dojścia pochodzą z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy i zawierają niezawodną <xref:System.Object.Finalize%2A> metody. Użycie bezpiecznego dojścia, należy po prostu zaimplementować <xref:System.IDisposable> interfejs i wywołać bezpiecznego dojścia <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in Class metoda swoje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. Finalizator bezpiecznego dojścia jest wywoływana automatycznie przez moduł odśmiecania pamięci jeśli jego <xref:System.IDisposable.Dispose%2A> nie jest wywoływana metoda.  
  
         —lub—  
  
    - Zastąp <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. Finalizacja umożliwia niedeterministyczne zwalnianie niezarządzanych zasobów, gdy konsument typu nie wywoła <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do usunięcia go w sposób deterministyczny. Jednak finalizacja obiektu może być złożoną i podatną na błędy operacją, więc zalecane jest używanie bezpiecznego dojścia, zamiast dostarczania własnego finalizatora.  
  
 Konsumenci typu będą następnie wywołać usługi <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji bezpośrednio w celu zwolnienia pamięci używanej przez niezarządzane zasoby. Po poprawnym zaimplementowaniu <xref:System.IDisposable.Dispose%2A> metody, albo bezpiecznego dojścia <xref:System.Object.Finalize%2A> metody lub zastąpienie metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda będzie odpowiadać za czyszczenie zasobów w przypadku gdy <xref:System.IDisposable.Dispose%2A> nie jest wywoływana metoda.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementacja metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 Opisuje sposób implementacji [wzorca usuwania](../../../docs/standard/design-guidelines/dispose-pattern.md) do zwalniania niezarządzanych zasobów.  
  
 [Używanie obiektów implementujących interfejs IDisposable](../../../docs/standard/garbage-collection/using-objects.md)  
 W tym artykule opisano, jak konsumenci typu upewnij się, że jego <xref:System.IDisposable.Dispose%2A> nosi nazwę wdrożenia. Firma Microsoft zaleca używanie C# `using` instrukcji lub Visual Basic `Using` instrukcję, aby to zrobić.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 Definiuje <xref:System.IDisposable.Dispose%2A> metodę służącą do zwalniania niezarządzanych zasobów.  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 Umożliwia finalizację obiektu, jeśli niezarządzane zasoby nie zostaną zwolnione za <xref:System.IDisposable.Dispose%2A> metody.  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 Pomija finalizację. Ta metoda jest zazwyczaj wywoływana z `Dispose` metodę, aby uniemożliwić wykonanie finalizatora.
