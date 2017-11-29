---
title: "Niezawodność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd13a09e66c865630b9db3210bbd95bab14cb214
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliability"></a>Niezawodność
Należy pamiętać, że wykonywanie kodu w środowisku serwerów, takich jak SQL Server ochronę przed asynchroniczne wyjątki. Niezawodność, zgodnie z opisem w tym miejscu nie jest specyficzne dla programu SQL Server, ale do pisania niezawodnej kodu dla każdego hosta w wersji programu .NET Framework 2.0 środowiska. Program SQL Server jest jednak pierwszej usługi wprowadzania szeroką gamę korzysta z nowych funkcji niezawodność w wersji 2.0, dlatego służy jako przykład.  
  
 Kodu uruchomionego w programie SQL Server musi uwzględniać bardziej rygorystyczne wytyczne niezawodność niż innych środowisk serwera. Jest to spowodowane operacja stałej programu SQL Server na brzegu zużycia zasobów.  <xref:System.OutOfMemoryException>i <xref:System.Threading.ThreadAbortException> wyjątków nie są rzadko w środowisku programu SQL Server. Wskazówki te zwykle są mniej ukierunkowanych na niezawodność i jeden na stosowanie pełni zaufany zarządzane niepowodzenie bezpiecznie face z kodu <xref:System.AppDomain>— poziom odtwarzania, sposób podstawowy serwer przechowuje spójności i dostępności.  
  
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
