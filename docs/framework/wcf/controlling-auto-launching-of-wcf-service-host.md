---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 806d85df2a7fff63704db755400b81cc2dc5c37b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652091"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Kontrolowanie automatycznego uruchamiania hosta programu WCF
Podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierającą wiele projektów, można kontrolować możliwości automatycznego uruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) w projekcie biblioteki usługi WCF.  
  
 Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona. Można wyczyść pole, tak aby Host usługi WCF dla tego określonego projektu nie jest uruchamiane, gdy inny projekt jest debugowany, w tym samym rozwiązaniu.  
  
 To zachowanie nie ma wpływu na debugowanie F5 lub funkcje Dodaj odwołanie do usługi dla tego projektu.  
  
 Ta opcja jest dostępna w następujących projektach:  
  
- Projekt biblioteki usługi WCF.  
  
- Projekt Biblioteka usługi sekwencyjnego przepływu pracy.  
  
- Projekt biblioteki usługi przepływu pracy automatu stanów.  
  
- Projekt Biblioteka usługi syndykacji.  
  
## <a name="see-also"></a>Zobacz także

- [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
