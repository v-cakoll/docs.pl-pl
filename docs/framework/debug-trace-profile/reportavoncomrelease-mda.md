---
title: reportAvOnComRelease MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de48fca818f8456627c9507756cc2d8a200c50e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
`reportAvOnComRelease` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy istnieją wyjątki zgłaszane z powodu użytkownika zliczanie błędów podczas wykonywania COM interop i użycie <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody połączone z pierwotnych wywołania COM.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu i uszkodzenie pamięci.  
  
## <a name="cause"></a>Przyczyna  
 Czasami jest zgłaszany wyjątek z powodu użytkownika zliczanie błędów podczas wykonywania COM interop i użycie <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody połączone z pierwotnych wywołania COM. Zazwyczaj tego wyjątku jest odrzucona, ponieważ nie w ten sposób spowodowałoby naruszenie zasad dostępu w środowisku CLR, wyłączania go. Po włączeniu tego Asystenta takie wyjątki można wykryte i zgłosił zamiast po prostu zostanie odrzucony.  
  
## <a name="resolution"></a>Rozwiązanie  
 Sprawdź, czy użytkownikowi zliczania kodu i wyszukać błędy, a także badanie klientach natywnych obiektu dla zliczanie błędów odwołań.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Dostępne są dwa tryby. Jeśli `allowAv` atrybutu `true`, Asystenta uniemożliwia środowiska uruchomieniowego odrzucanie naruszenia zasad dostępu. Jeśli `allowAv` jest `false`, co jest ustawieniem domyślnym, środowisko uruchomieniowe odrzuca naruszenia zasad dostępu, ale komunikat ostrzegawczy jest zgłaszany użytkownikowi wskazująca, czy wyjątek został zgłoszony i odrzucone.  
  
## <a name="output"></a>Dane wyjściowe  
 Jeśli to możliwe dane wyjściowe zawierają oryginalnego vtable wskaźnika interfejsu COM. W przeciwnym razie zostanie wyświetlony komunikat informacyjny.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
