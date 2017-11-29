---
title: "Oczyszczanie zasobów niezarządzanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c94a449edbbe38c4028e27fd946b66a054badf51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cleaning-up-unmanaged-resources"></a>Oczyszczanie zasobów niezarządzanych
W większości obiektów tworzonych przez aplikację może polegać na. Moduł zbierający elementy bezużyteczne w sieci do obsługi zarządzania pamięcią. Jeśli jednak są tworzone obiekty zawierające niezarządzane zasoby, należy jawnie zwalniać te zasoby po zakończeniu używania ich w aplikacji. Najpopularniejsze typy niezarządzanych zasobów to obiekty, które umieszczają w otoce zasoby systemu operacyjnego, takie jak pliki, okna, połączenia sieciowe lub połączenia bazy danych. Mimo że moduł odśmiecania pamięci jest w stanie śledzić okres istnienia obiektu hermetyzującego niezarządzany zasób, nie ma informacji, jak zwolnić i wyczyścić niezarządzany zasób.  
  
 Jeśli typy w aplikacji używają niezarządzanych zasobów, należny wykonać następujące czynności:  
  
-   Implementowanie [wzorzec dispose](../../../docs/standard/design-guidelines/dispose-pattern.md). Wymaga to podania <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji, aby włączyć deterministyczne wersji zasoby niezarządzane. Klient korzystający z wywołania typu <xref:System.IDisposable.Dispose%2A> po obiektu (i wykorzystuje zasoby) nie jest już potrzebne. <xref:System.IDisposable.Dispose%2A> Metody natychmiast zwalnia zasoby niezarządzane.  
  
-   Przewidują niezarządzane zasoby do zwolnienia w przypadku, gdy klient tego typu zapomni do wywołania <xref:System.IDisposable.Dispose%2A>. Istnieją dwa sposoby wykonania tej czynności:  
  
    -   Użycie bezpiecznego dojścia w celu umieszczenie niezarządzanego zasobu w otoce. Jest to zalecana technika. Pochodne bezpiecznego dojścia <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy i obejmują niezawodne <xref:System.Object.Finalize%2A> — metoda. Korzystając z bezpieczne dojście, po prostu zaimplementowaniem <xref:System.IDisposable> interfejsu i Wywołaj bezpieczne dojście <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> metody w Twojej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. Bezpieczne dojście finalizatora jest wywoływana automatycznie przez moduł garbage collector jeśli jego <xref:System.IDisposable.Dispose%2A> nie jest wywoływana metoda.  
  
         —lub—  
  
    -   Zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. Finalizacji umożliwia deterministyczna wersji zasoby niezarządzane, gdy konsumenta typu nie można wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do usuwania z nich w sposób niejednoznaczny. Jednak finalizacja obiektu może być złożoną i podatną na błędy operacją, więc zalecane jest używanie bezpiecznego dojścia, zamiast dostarczania własnego finalizatora.  
  
 Konsumenci tego typu można wywoływać z <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację bezpośrednio, aby zwolnić pamięć, używany przez zasoby niezarządzane. Gdy prawidłowo zaimplementować <xref:System.IDisposable.Dispose%2A> metody, albo bezpieczne dojście <xref:System.Object.Finalize%2A> metody lub zastąpienia z <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody staje się zabezpieczenia, aby wyczyścić zasoby w przypadku gdy <xref:System.IDisposable.Dispose%2A> nie wywołano metody.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementacja metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 Opisuje sposób wdrożenia [wzorzec dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) za zwolnienie niezarządzanych zasobów.  
  
 [Używanie obiektów implementujących interfejs IDisposable](../../../docs/standard/garbage-collection/using-objects.md)  
 W tym artykule opisano, jak konsumentów typu upewnij się, że jego <xref:System.IDisposable.Dispose%2A> nosi nazwę wdrożenia. Firma Microsoft zaleca używanie języka C# `using` instrukcji lub Visual Basic `Using` instrukcji w tym celu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 Definiuje <xref:System.IDisposable.Dispose%2A> metoda zwalniania niezarządzanych zasobów.  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 W przypadku niezarządzanych zasobów nie są wydawane przez zapewnia dla obiekt finalizacji <xref:System.IDisposable.Dispose%2A> metody.  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 Pomija finalizację. Ta metoda jest zazwyczaj wywoływana z `Dispose` metodę, aby zapobiec finalizator wykonywania.
