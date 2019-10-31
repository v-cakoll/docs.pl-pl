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
ms.openlocfilehash: 9e93f07b3b84264373db0317919b6ee519c8127c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138049"
---
# <a name="foreground-and-background-threads"></a>Wątki pierwszego planu i tła
Zarządzany wątek jest wątkiem w tle lub wątkiem pierwszego planu. Wątki w tle są takie same jak wątki pierwszego planu z jednym wyjątkiem: wątek w tle nie utrzymuje uruchomionego środowiska wykonywania zarządzanego. Po zatrzymaniu wszystkich wątków pierwszego planu w procesie zarządzanym (gdzie plik exe jest zestawem zarządzanym) system zatrzymuje wszystkie wątki w tle i zamyka.  
  
> [!NOTE]
> Gdy środowisko uruchomieniowe zatrzyma wątek w tle, ponieważ trwa zamykanie procesu, w wątku nie jest zgłaszany żaden wyjątek. Jeśli jednak wątki są zatrzymane, ponieważ metoda <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zwalnia domenę aplikacji, <xref:System.Threading.ThreadAbortException> jest generowany zarówno w wątku na pierwszym planie, jak i w tle.  
  
 Użyj właściwości <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>, aby określić, czy wątek to tło, czy wątek pierwszego planu czy zmienić jego stan. Wątek można w dowolnym momencie zmienić na wątek w tle przez ustawienie jego właściwości <xref:System.Threading.Thread.IsBackground%2A> na `true`.  
  
> [!IMPORTANT]
> Stan pierwszego planu lub tła wątku nie wpływa na wynik nieobsługiwanego wyjątku w wątku. W .NET Framework w wersji 2,0, nieobsłużony wyjątek w wątkach na pierwszym planie lub w tle powoduje zakończenie działania aplikacji. Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Wątki należące do puli wątków zarządzanych (czyli wątki, których właściwość <xref:System.Threading.Thread.IsThreadPoolThread%2A> jest `true`) są wątkami w tle. Wszystkie wątki, które wprowadzają zarządzane środowisko wykonawcze z kodu niezarządzanego, są oznaczane jako wątki w tle. Wszystkie wątki wygenerowane przez tworzenie i uruchamianie nowego obiektu <xref:System.Threading.Thread> są domyślnie wątki pierwszego planu.  
  
 Jeśli użyjesz wątku do monitorowania działania, takiego jak połączenie gniazda, ustaw jej Właściwość <xref:System.Threading.Thread.IsBackground%2A> na `true`, aby wątek nie uniemożliwił przerwania procesu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
