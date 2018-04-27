---
title: Wskazówki dotyczące migracji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11a4b1d6665e0198f8c9afc0209e9fb09cc599ad
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="migration-guidance"></a>Wskazówki dotyczące migracji
W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], firma Microsoft udostępnia drugą wersją główną systemu Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] została wydana w [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (to uwzględnione typy w przestrzeniach nazw System.Workflow.*; teraz nazywane WF3) i rozszerzony w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 jest również częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale istnieją obok nowej technologii przepływu pracy (typy węzła System.Activities.\* przestrzeni nazw; określone jako WF4). Podczas określania, kiedy należy przyjąć WF4, należy najpierw rozpoznaje, że kontrolować czas.  
  
-   WF3 jest w pełni obsługiwane częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   Aplikacje WF3 działać na [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez żadnych modyfikacji i nadal w pełni obsługiwane.  
  
-   Można tworzyć nowe aplikacje WF3 i istniejące aplikacje mogą być edytowane w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i są w pełni obsługiwane.  
  
 W związku z tym decyzji o przyjęciu programu .NET Framework 4 jest całkowicie niezależna od programu decyzji o przeniesieniu na WF4 (System.Activities.*) z WF3 (System.Workflow.\*). Ten temat zawiera łącza do wskazówek dotyczących migracji WF, który zawiera informacje o pracy z WF3 i WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Oficjalne dokumenty programu WF migracji i Cookbooks  
 [Omówienie migracji WF](http://go.microsoft.com/fwlink/?LinkId=153873) temat zawiera ogólne omówienie relacji między strategie WF3 i WF4 i migracji. Tematy uzupełniające przejść do szczegółów w określonych tematów.  
  
 [Omówienie migracji WF](http://go.microsoft.com/fwlink/?LinkId=153873)  
 Opisuje relację między WF3 i WF4 i opcje, które mają jako użytkownik lub potencjalne przepływu pracy technologii .NET 4.  
  
 [Migracja WF: Najlepsze rozwiązania dotyczące WF3 programowanie](http://go.microsoft.com/fwlink/?LinkId=153852)  
 W tym artykule omówiono sposób projektowania artefakty WF3, dlatego może być łatwiej migracji do WF4.  
  
 [Wskazówki dotyczące WF: reguły](http://go.microsoft.com/fwlink/?LinkId=153854)  
 Omówiono sposoby dostosowania związane z reguły inwestycji do przodu do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] rozwiązania.  
  
 [Wskazówki dotyczące WF: Automatu stanów](http://go.microsoft.com/fwlink/?LinkId=153855)  
 W tym artykule omówiono przepływ sterowania WF4 modelowania w przypadku braku aktywności komputera stanu.  
  
 Należy pamiętać, że w tych wskazówkach dotyczy tylko projektów przepływu pracy, które odnoszą się do programu .NET Framework 4. Stan pracy maszyny zostały dodane w programie .NET 4.0.1 wraz z wydaniem Platform Update 1 i zostały zawarte w ramach programu .NET Framework 4.5. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Stan maszyny z przepływów pracy w programie .NET 4.0.1 — 4.0.3 i .NET Framework 4.5, zobacz [aktualizacji dla programu Microsoft .NET Framework 4 funkcji 4.0.1](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) i [przepływy pracy maszyny stanu](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
 [WF Cookbook migracji: Niestandardowe działania](http://go.microsoft.com/fwlink/?LinkId=153856)  
 Zawiera instrukcje dotyczące zmiany projektu WF3 niestandardowych działań na WF4 i przykłady.  
  
 [Programu WF Cookbook migracji: Zaawansowane niestandardowych działań](http://go.microsoft.com/fwlink/?LinkId=275560)  
 Zawiera wskazówki dotyczące zmodyfikowanie zaawansowanych WF3 niestandardowych działań korzystających z kolejek WF3 i harmonogram działania podrzędne jako WF4 działań niestandardowych.  
  
 [WF migracji Cookbook: przepływów pracy](http://go.microsoft.com/fwlink/?LinkId=153858)  
 Zawiera instrukcje dotyczące zmiany projektu przepływów pracy WF3 na WF4 i przykłady.  
  
 [WF Cookbook migracji: Hosting przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=275561)  
 Zawiera wskazówki dotyczące zmodyfikowanie kodu hostingu WF3 jako kod obsługi WF4. Celem jest, aby pokrywał się podstawowe różnice w przepływie pracy hosting między WF3 i WF4.  
  
 [WF Cookbook migracji: Śledzenie przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=275562)  
 Zawiera wskazówki dotyczące zmiany projektu kod śledzenia WF3 i konfiguracji przy użyciu równoważne WF4 kod śledzenia i konfiguracji.  
  
 [WF wskazówek: Usługi przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=275564)  
 Udostępnia zorientowane na przykład szczegółowe instrukcje dotyczące zmiany projektu przepływy pracy, które implementują Windows Communication Foundation (WCF) usługi sieci web (nazywane usług przepływu pracy) utworzone w WF3 WF4, na potrzeby typowych scenariuszy dla out-of-box działania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.Interop>
