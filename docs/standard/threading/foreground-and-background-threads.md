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
ms.openlocfilehash: 476dc75a569224db405eb7498ecb35eb6bda24d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583080"
---
# <a name="foreground-and-background-threads"></a>Wątki pierwszego planu i tła
Zarządzane wątek jest wątku w tle lub wątku pierwszego planu. Wątki w tle są takie same jak wątki pierwszoplanowe z jednym wyjątkiem: wątku w tle nie przechowuje zarządzanego środowiska wykonawczego uruchomiona. Po w procesie zarządzanych (gdzie plik .exe jest zestaw zarządzany) zostały zatrzymane wszystkie wątki pierwszego planu, system zatrzymuje wszystkie wątki w tle i zamyka.  
  
> [!NOTE]
>  Środowisko uruchomieniowe zatrzymania wątku w tle, ponieważ trwa zamykanie procesu, nie jest wyjątek w wątku. Jednak gdy wątki są zatrzymane, ponieważ <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda zwalnia domeny aplikacji <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątkach tła i pierwszego planu.  
  
 Użyj <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> właściwości, aby określić, czy wątek jest tło lub wątku pierwszego planu lub zmienić jego stan. Wątek, który można zmienić na wątku w tle w dowolnym momencie przez ustawienie jej <xref:System.Threading.Thread.IsBackground%2A> właściwości `true`.  
  
> [!IMPORTANT]
>  Pierwszym planie lub w tle stan wątku nie ma wpływu na wynik nieobsługiwany wyjątek w wątku. Wystąpił nieobsługiwany wyjątek w wątkach na pierwszym planie lub w tle w programie .NET Framework w wersji 2.0, powoduje Kończenie działania aplikacji. Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Wątków, które należą do puli wątków zarządzanych (to znaczy, których wątki <xref:System.Threading.Thread.IsThreadPoolThread%2A> jest właściwość `true`) są wątki w tle. Wprowadź zarządzanego środowiska wykonawczego z kodem niezarządzanym wszystkie wątki są oznaczone jako wątki w tle. Wszystkie wątki generowane przez tworzenie i uruchamianie nowej <xref:System.Threading.Thread> obiektu są przez wątki pierwszoplanowe domyślne.  
  
 Jeśli wątek służą do monitorowania działania, takie jak połączenia gniazda, ustaw jej <xref:System.Threading.Thread.IsBackground%2A> właściwości `true` , dzięki czemu wątek nie uniemożliwia zakończenie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
