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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138049"
---
# <a name="foreground-and-background-threads"></a>Wątki pierwszego planu i tła
Wątek zarządzany jest wątkiem tła lub wątku pierwszego planu. Wątki w tle są identyczne z wątków pierwszego planu z jednym wyjątkiem: wątek w tle nie prowadzi zarządzanego środowiska wykonawczego uruchomione. Po zatrzymaniu wszystkich wątków pierwszego planu w procesie zarządzanym (gdzie plik exe jest zarządzanym zestawem), system zatrzymuje wszystkie wątki w tle i zamyka.  
  
> [!NOTE]
> Gdy środowiska uruchomieniowego zatrzymuje wątek w tle, ponieważ proces jest zamykany, nie wyjątek w wątku. Jednak gdy wątki są <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zatrzymane, ponieważ metoda zwalnia <xref:System.Threading.ThreadAbortException> domeny aplikacji, a jest generowany zarówno w wątkach pierwszego planu i tła.  
  
 Użyj <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> właściwości, aby ustalić, czy wątek jest tłem lub wątkiem pierwszego planu, czy zmienić jego stan. Wątek można zmienić na wątek w tle w <xref:System.Threading.Thread.IsBackground%2A> dowolnym `true`momencie, ustawiając jego właściwość na .  
  
> [!IMPORTANT]
> Pierwszy plan lub stan tła wątku nie ma wpływu na wynik nieobsługiwanego wyjątku w wątku. W .NET Framework w wersji 2.0 nieobsługiwany wyjątek w wątkach pierwszego planu lub tła powoduje zakończenie aplikacji. Zobacz [wyjątki w wątkach zarządzanych](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Wątki, które należą do puli wątków zarządzanych (czyli wątków, których <xref:System.Threading.Thread.IsThreadPoolThread%2A> właściwość jest `true`) są wątki w tle. Wszystkie wątki, które wchodzą do środowiska wykonawczego zarządzanego z kodu niezarządzanego są oznaczone jako wątki w tle. Wszystkie wątki generowane przez tworzenie <xref:System.Threading.Thread> i uruchamianie nowego obiektu są domyślnie wątków pierwszego planu.  
  
 Jeśli używasz wątku do monitorowania działania, takich jak <xref:System.Threading.Thread.IsBackground%2A> połączenie `true` gniazda, należy ustawić jego właściwość tak, aby wątek nie uniemożliwia zakończenia procesu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
