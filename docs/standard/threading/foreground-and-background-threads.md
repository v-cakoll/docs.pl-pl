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
ms.openlocfilehash: fcedd478ee1eb89c11dc9535b1d2ffe843d0f658
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081332"
---
# <a name="foreground-and-background-threads"></a>Wątki pierwszego planu i tła
Wątek jest wątku w tle lub wątku na pierwszym planie. Wątków w tle są takie same, wątki pierwszoplanowe z jednym wyjątkiem: wątku w tle nie przechowuje zarządzanym środowisku wykonywania uruchomiona. Gdy wszystkie wątki pierwszoplanowe zostały zatrzymane w ramach procesu zarządzanego (gdzie plik .exe jest zarządzanym zestawem), system zatrzymuje wszystkich wątków w tle i zamyka.  
  
> [!NOTE]
>  Środowisko uruchomieniowe zatrzymania wątku w tle, ponieważ trwa zamykanie procesu, jest zgłaszany żaden wyjątek w wątku. Jednak gdy wątki są zatrzymane, ponieważ <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda zwalnia domeny aplikacji <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątki pierwszego planu i tła.  
  
 Użyj <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> właściwości, aby określić, czy wątek jest tło lub wątku na pierwszym planie lub zmienić jego stan. Wątek, który można zmienić na wątku w tle w dowolnym momencie przez ustawienie jego <xref:System.Threading.Thread.IsBackground%2A> właściwość `true`.  
  
> [!IMPORTANT]
>  Pierwszy plan lub tło stan wątku nie ma wpływu na wynik nieobsługiwany wyjątek w wątku. W programie .NET Framework 2.0 nieobsługiwanego wyjątku w wątki pierwszego planu i tła powoduje zakończenia aplikacji. Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Wątki, które należą do puli wątków zarządzanych (oznacza to, wątki, których <xref:System.Threading.Thread.IsThreadPoolThread%2A> właściwość `true`) są wątków w tle. Wszystkie wątki, które wprowadzać środowiska wykonawczego zarządzanych z niezarządzanego kodu są oznaczone jako wątków w tle. Wszystkie wątki, generowane przez tworzenie i uruchamianie nowego <xref:System.Threading.Thread> obiektu są przez domyślne, wątki pierwszego planu.  
  
 Jeśli używasz wątku monitorować działania, takie jak połączenia z gniazdem, ustawić jej <xref:System.Threading.Thread.IsBackground%2A> właściwość `true` tak, aby wątek nie uniemożliwia zakończenie procesu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadAbortException>
