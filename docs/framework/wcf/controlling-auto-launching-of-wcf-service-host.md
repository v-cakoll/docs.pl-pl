---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320625"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Kontrolowanie automatycznego uruchamiania hosta programu WCF
Można kontrolować funkcję autouruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost. exe) dla projektu biblioteki usług WCF, podczas debugowania innego projektu w tym samym rozwiązaniu programu Visual Studio zawierającym wiele projektów.  
  
 Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksplorator rozwiązań**, wybierz polecenie **Właściwości**, a następnie kliknij kartę **Opcje WCF** . **Uruchom hosta usługi WCF podczas debugowania innego projektu w tym samym rozwiązaniu** pole wyboru jest domyślnie włączone. Możesz wyczyścić to pole, aby Host usługi WCF dla danego projektu nie był uruchamiany, gdy inny projekt jest debugowany w tym samym rozwiązaniu.  
  
 To zachowanie nie ma wpływu na Debugowanie F5 ani Dodaj odwołanie do usługi funkcji dla tego projektu.  
  
 Ta opcja jest dostępna dla następujących projektów:  
  
- Projekt biblioteki usług WCF.  
  
- Projekt biblioteki usługi sekwencyjnego przepływu pracy.  
  
- Projekt biblioteki usługi przepływu pracy automatu Stanów.  
  
- Projekt biblioteki usługi zespolonej.  
  
## <a name="see-also"></a>Zobacz także

- [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
