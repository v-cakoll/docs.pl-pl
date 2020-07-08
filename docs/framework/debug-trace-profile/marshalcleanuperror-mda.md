---
title: marshalCleanupError MDA
description: Przejrzyj marshalCleanupError Managed Debug Assistant (MDA), który jest wywoływany ze względu na to, że wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051614"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
`marshalCleanupError`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby oczyszczenia tymczasowych struktur i pamięci używanej do organizowania typów danych między natywnymi i zarządzanymi granicami kodu.  
  
## <a name="symptoms"></a>Objawy  
 Przeciek pamięci występuje podczas wykonywania natywnych i zarządzanych przejść do kodu, stan środowiska uruchomieniowego, taki jak kultura wątku nie jest przywracany lub błędy pojawiają się w wyniku <xref:System.Runtime.InteropServices.SafeHandle> czyszczenia.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przejrzyj wszystkie <xref:System.Runtime.InteropServices.SafeHandle> implementacje destruktora, finalizatora i niestandardowego organizatora pod kątem błędów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat zgłaszający operację, która nie powiodła się podczas czyszczenia.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
