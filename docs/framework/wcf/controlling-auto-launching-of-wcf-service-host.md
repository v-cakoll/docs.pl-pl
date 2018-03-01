---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Kontrolowanie automatycznego uruchamiania hosta programu WCF
Można kontrolować możliwości automatycznego uruchamiania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hosta usługi (WcfSvcHost.exe) dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu biblioteki usługi, podczas debugowania innego projektu w tym samym [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] rozwiązanie zawierające wiele projektów.  
  
 Aby to zrobić, kliknij prawym przyciskiem myszy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projekt usługi w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona. Możesz usunąć zaznaczenie pola, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi dla tego konkretnego projektu nie jest uruchamiane podczas debugowania innego projektu w tym samym rozwiązaniu.  
  
 To zachowanie nie ma wpływu na debugowanie F5 lub funkcji Dodaj odwołanie do usługi dla tego projektu.  
  
 Ta opcja jest dostępna w następujących projektach:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Projekt biblioteki usługi.  
  
-   Projekt biblioteki usługi sekwencyjnego przepływu pracy.  
  
-   Projekt biblioteki usługi przepływu pracy automatu stanów.  
  
-   Projekt biblioteki usługi zespolonego.  
  
## <a name="see-also"></a>Zobacz też  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
