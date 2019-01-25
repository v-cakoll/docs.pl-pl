---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f7f58a684449819fe945ad1ba5bff12f425c8294
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712395"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Kontrolowanie automatycznego uruchamiania hosta programu WCF
Podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierającą wiele projektów, można kontrolować możliwości automatycznego uruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) w projekcie biblioteki usługi WCF.  
  
 Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona. Można wyczyść pole, tak aby Host usługi WCF dla tego określonego projektu nie jest uruchamiane, gdy inny projekt jest debugowany, w tym samym rozwiązaniu.  
  
 To zachowanie nie ma wpływu na debugowanie F5 lub funkcje Dodaj odwołanie do usługi dla tego projektu.  
  
 Ta opcja jest dostępna w następujących projektach:  
  
-   Projekt biblioteki usługi WCF.  
  
-   Projekt Biblioteka usługi sekwencyjnego przepływu pracy.  
  
-   Projekt biblioteki usługi przepływu pracy automatu stanów.  
  
-   Projekt Biblioteka usługi syndykacji.  
  
## <a name="see-also"></a>Zobacz także
- [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
