---
title: Niezawodność
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b00ba0fdf732a864fb4fb757c6012a3d36740b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949295"
---
# <a name="reliability"></a>Niezawodność
Należy pamiętać, że kodu wykonywanego w środowisku serwerów, takich jak SQL Server ochronę przed wyjątki asynchroniczne. Niezawodność, zgodnie z opisem w tym miejscu nie jest specyficzne dla programu SQL Server, ale do pisania niezawodne kodu dla każdego hosta w .NET Framework w wersji 2.0 środowiska. Program SQL Server jest jednak pierwszej usługi tworzenie rozległe Użyj nowych funkcji niezawodność w wersji 2.0, dzięki czemu jest ona używana jako przykład.  
  
 Kod uruchomiony w programie SQL Server muszą radzić sobie z bardziej rygorystyczne wytyczne niezawodność niż innych środowisk serwera. Jest to spowodowane działania stały programu SQL Server na urządzeniach brzegowych zużycia zasobów.  <xref:System.OutOfMemoryException> i <xref:System.Threading.ThreadAbortException> wyjątki nie są niczym niezwykłym w środowisku programu SQL Server. Te wytyczne są ogólnie rzecz biorąc mniej ukierunkowane na niezawodność i więcej w umożliwiając całkowicie zaufanym zarządzanemu kodowi elegancko nie powieść się face z <xref:System.AppDomain>— poziom odtwarzania, który jest podstawowym sposobem server zachowuje spójności i dostępności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Atrybuty ochrony hosta i programowanie SQL Server](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 W tym artykule opisano sposób, w jaki <xref:System.Security.Permissions.HostProtectionAttribute> atrybut jest używany przez program SQL Server, aby ograniczyć wykonywanie kodu zarządzanego.  
  
 [Najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md)  
 Wskazówki dotyczące pisania kodu, który spełnia wymagania dotyczące niezawodności.  
  
 [Ograniczone regiony wykonania](../../../docs/framework/performance/constrained-execution-regions.md)  
 Zawiera opis funkcji i zachowania ograniczone regiony wykonania (CERs).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
