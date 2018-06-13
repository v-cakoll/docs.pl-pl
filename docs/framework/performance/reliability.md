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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395414"
---
# <a name="reliability"></a>Niezawodność
Należy pamiętać, że wykonywanie kodu w środowisku serwerów, takich jak SQL Server ochronę przed asynchroniczne wyjątki. Niezawodność, zgodnie z opisem w tym miejscu nie jest specyficzne dla programu SQL Server, ale do pisania niezawodnej kodu dla każdego hosta w wersji programu .NET Framework 2.0 środowiska. Program SQL Server jest jednak pierwszej usługi wprowadzania szeroką gamę korzysta z nowych funkcji niezawodność w wersji 2.0, dlatego służy jako przykład.  
  
 Kodu uruchomionego w programie SQL Server musi uwzględniać bardziej rygorystyczne wytyczne niezawodność niż innych środowisk serwera. Jest to spowodowane operacja stałej programu SQL Server na brzegu zużycia zasobów.  <xref:System.OutOfMemoryException> i <xref:System.Threading.ThreadAbortException> wyjątków nie są rzadko w środowisku programu SQL Server. Wskazówki te zwykle są mniej ukierunkowanych na niezawodność i jeden na stosowanie pełni zaufany zarządzane niepowodzenie bezpiecznie face z kodu <xref:System.AppDomain>— poziom odtwarzania, sposób podstawowy serwer przechowuje spójności i dostępności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Atrybuty ochrony hosta i programowanie SQL Server](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Opisuje sposób <xref:System.Security.Permissions.HostProtectionAttribute> atrybut jest używany przez program SQL Server do ograniczania wykonywanie kodu zarządzanego.  
  
 [Najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md)  
 Wskazówki dotyczące pisania kodu, który spełnia wymagania dotyczące niezawodności.  
  
 [Ograniczone regiony wykonania](../../../docs/framework/performance/constrained-execution-regions.md)  
 Zawiera opis funkcji i zachowanie ograniczone regiony wykonania (CERs).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
