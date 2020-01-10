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
ms.openlocfilehash: 2d6601c4cbad32f768ff16301307083f35d986a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715970"
---
# <a name="reliability"></a>Niezawodność
Ważne jest, aby kod wykonywany w środowiskach serwerów, takich jak SQL Server chronić przed wyjątkami asynchronicznymi. Niezawodność, zgodnie z opisem w tym miejscu, nie jest specyficzna dla SQL Server, ale do pisania niezawodnego kodu dla dowolnego hosta wykonywanego w środowisku .NET Framework w wersji 2,0. Jednak SQL Server to pierwsza usługa, która korzysta z nowych funkcji zapewniających niezawodność w wersji 2,0, więc jest używana jako przykład.  
  
 Kod działający w SQL Server musi obsłużyć bardziej rygorystyczne wytyczne dotyczące niezawodności niż inne środowiska serwera. Jest to spowodowane ciągłą operacją SQL Server na granicy zużycia zasobów.  wyjątki <xref:System.OutOfMemoryException> i <xref:System.Threading.ThreadAbortException> nie są rzadko w środowisku SQL Server. Ogólnie rzecz biorąc, te wytyczne mają mniej informacji na temat niezawodności i więcej na umożliwienie w pełni zaufanego kodu zarządzanego, aby zapewnić bezproblemowy błąd podczas odtwarzania na poziomie <xref:System.AppDomain>, który jest głównym sposobem, w jaki serwer utrzymuje spójność i dostępność.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Atrybuty ochrony hosta i programowanie SQL Server](sql-server-programming-and-host-protection-attributes.md)  
 Opisuje, w jaki sposób atrybut <xref:System.Security.Permissions.HostProtectionAttribute> jest używany przez SQL Server do ograniczania wykonywania kodu zarządzanego.  
  
 [Najlepsze rozwiązania dotyczące niezawodności](reliability-best-practices.md)  
 Zawiera wytyczne dotyczące pisania kodu, który spełnia wymagania dotyczące niezawodności.  
  
 [Ograniczone regiony wykonania](constrained-execution-regions.md)  
 Opisuje funkcję i zachowanie regionów ograniczonego wykonywania (CERs).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
