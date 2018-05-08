---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: fe936ee3ff42b586c733de597de808b86f3e2575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Kontrolowanie automatycznego uruchamiania hosta programu WCF
Można kontrolować możliwość automatycznego uruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu biblioteki usługi, podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierający wiele projektów .  
  
 Aby to zrobić, kliknij prawym przyciskiem myszy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projekt usługi w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona. Możesz usunąć zaznaczenie pola, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi dla tego konkretnego projektu nie jest uruchamiane podczas debugowania innego projektu w tym samym rozwiązaniu.  
  
 To zachowanie nie ma wpływu na debugowanie F5 lub funkcji Dodaj odwołanie do usługi dla tego projektu.  
  
 Ta opcja jest dostępna w następujących projektach:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projekt biblioteki usługi.  
  
-   Projekt biblioteki usługi sekwencyjnego przepływu pracy.  
  
-   Projekt biblioteki usługi przepływu pracy automatu stanów.  
  
-   Projekt biblioteki usługi zespolonego.  
  
## <a name="see-also"></a>Zobacz też  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
