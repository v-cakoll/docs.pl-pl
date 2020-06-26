---
title: Włączanie debugowania dołączania JIT
description: Włącz debugowanie w czasie just-in Time (JIT), aby dołączyć debuger do procesu w przypadku wystąpienia błędów. Może być wyzwalane przez niektóre metody lub funkcje.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416047"
---
# <a name="enabling-jit-attach-debugging"></a>Włączanie debugowania dołączania JIT
Debugowanie z dołączaniem JIT jest frazą używaną do opisywania dołączania debugera do procesu w przypadku wystąpienia błędów lub może być wyzwalane przez określone metody lub funkcje.  
  
 Debugowanie dołączania JIT jest używane w następujących warunkach błędu:  
  
- Nieobsłużone wyjątki (zarówno w kodzie macierzystym, jak i zarządzanym).  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda lub funkcja [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (rodzina systemu Windows 7).  
  
- Błędy krytyczne środowiska uruchomieniowego.  
  
 Debugowanie dołączania JIT jest również wyzwalane przez wywołania następujących metod i funkcji:  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Method.  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Method.  
  
- Funkcja [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).  
  
 Przed .NET Framework 4 .NET Framework podano oddzielne klucze rejestru, aby kontrolować zachowanie debugera natywnego i zarządzanego. Począwszy od .NET Framework 4, formant jest konsolidowany pod pojedynczym kluczem rejestru: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Wartości, które można ustawić dla tego klucza, określają, czy jest wywoływany debuger, i, jeśli tak, to czy jest wywoływany przy użyciu okna dialogowego, które wymaga interakcji z użytkownikiem. Informacje o ustawianiu tego klucza rejestru można znaleźć w temacie [Configuring Automatic Debug](/windows/win32/debug/configuring-automatic-debugging).  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie, śledzenie i profilowanie](index.md)
- [Ułatwianie debugowania obrazu](making-an-image-easier-to-debug.md)
