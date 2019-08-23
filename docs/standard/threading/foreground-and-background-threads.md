---
title: Wątki pierwszego planu i tła
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dbad5da42f5ed4e03751534a3a183615a9757cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960023"
---
# <a name="foreground-and-background-threads"></a>Wątki pierwszego planu i tła
Zarządzany wątek jest wątkiem w tle lub wątkiem pierwszego planu. Wątki w tle są takie same jak wątki pierwszego planu z jednym wyjątkiem: wątek w tle nie utrzymuje uruchomionego środowiska wykonywania zarządzanego. Po zatrzymaniu wszystkich wątków pierwszego planu w procesie zarządzanym (gdzie plik exe jest zestawem zarządzanym) system zatrzymuje wszystkie wątki w tle i zamyka.  
  
> [!NOTE]
> Gdy środowisko uruchomieniowe zatrzyma wątek w tle, ponieważ trwa zamykanie procesu, w wątku nie jest zgłaszany żaden wyjątek. Jeśli jednak wątki są zatrzymane <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadAbortException> , ponieważ metoda zwalnia domenę aplikacji, jest zgłaszany zarówno w wątku na pierwszym planie, jak i w tle.  
  
 Użyj właściwości <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> , aby określić, czy wątek jest wątkiem w tle, czy na pierwszym planie czy zmienić jego stan. Wątek można w dowolnym momencie zmienić na wątek w tle przez ustawienie jego <xref:System.Threading.Thread.IsBackground%2A> właściwości na. `true`  
  
> [!IMPORTANT]
> Stan pierwszego planu lub tła wątku nie wpływa na wynik nieobsługiwanego wyjątku w wątku. W .NET Framework w wersji 2,0, nieobsłużony wyjątek w wątkach na pierwszym planie lub w tle powoduje zakończenie działania aplikacji. Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Wątki należące do puli wątków zarządzanych (czyli wątki, których <xref:System.Threading.Thread.IsThreadPoolThread%2A> właściwość jest `true`) są wątkami w tle. Wszystkie wątki, które wprowadzają zarządzane środowisko wykonawcze z kodu niezarządzanego, są oznaczane jako wątki w tle. Wszystkie wątki wygenerowane przez tworzenie i uruchamianie nowego <xref:System.Threading.Thread> obiektu są domyślnie wątki pierwszego planu.  
  
 Jeśli użyjesz wątku do monitorowania działania, takiego jak połączenie gniazda, ustaw jego <xref:System.Threading.Thread.IsBackground%2A> właściwość na `true` tak, aby wątek nie uniemożliwił przerwania procesu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
