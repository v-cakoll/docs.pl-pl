---
title: Włączanie debugowania dołączania JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b92592500f0babf29891710cedf1228b0ddcb0e4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616880"
---
# <a name="enabling-jit-attach-debugging"></a>Włączanie debugowania dołączania JIT
Debugowania dołączania JIT jest wyrażenie używane do opisywania dołączanie debugera do procesu, gdy wystąpią błędy lub mogą być wyzwalane przez określone metody lub funkcji.  
  
 Debugowania dołączania JIT jest używany w następujących warunkach błędów:  
  
-   Nieobsługiwane wyjątki (w kodzie natywnych i zarządzanych).  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Metoda lub [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) — funkcja (Windows 7 rodzina).  
  
-   Błędy krytyczne środowiska uruchomieniowego.  
  
 Debugowania dołączania JIT jest również wyzwalany przez wywołania do następujących metod i funkcji:  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> Metoda.  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> Metoda.  
  
-   [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) — funkcja (Win32).  
  
 Przed [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework podane klucze rejestru oddzielne, aby kontrolować zachowanie natywnych i zarządzanych debugerów. Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kontrolki są konsolidowane w kluczu rejestru pojedynczego: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Wartości, które można ustawić dla tego klucza określają, czy debuger jest wywoływany, a jeśli tak, czy jest wywoływana z okna dialogowego wymaga interakcji użytkownika. Aby uzyskać informacji o ustawieniu tego klucza rejestru, zobacz [Konfigurowanie automatycznego debugowania](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, śledzenie i profilowanie](../../../docs/framework/debug-trace-profile/index.md)  
 [Ułatwianie debugowania obrazu](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [Włączanie profilowania](https://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
