---
title: Wskazówki dotyczące migracji
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 73488354a807d8bf7d90c97b95f1021d884efd27
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777961"
---
# <a name="migration-guidance"></a>Wskazówki dotyczące migracji
W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], firma Microsoft udostępnia drugą wersją główną systemu Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] został wydany w [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (to uwzględnione typy w przestrzeniach nazw System.Workflow.*; teraz nazywana WF3) i ulepszone w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 jest również częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale istnieje się wraz z technologią przepływu pracy (typy System.Activities.\* obszarów nazw; nazywane WF4). Podczas wybierania, kiedy należy przyjąć WF4, należy najpierw rozpoznaje, że możesz kontrolować termin.  
  
-   WF3 jest w pełni obsługiwana częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   WF3 aplikacje są uruchamiane w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez żadnych modyfikacji i w dalszym ciągu można w pełni obsługiwane.  
  
-   Można tworzyć nowe aplikacje WF3 i istniejących aplikacji można edytować w programie Visual Studio 2012 i są w pełni obsługiwane.  
  
 W efekcie decyzji o przyjęciu programu .NET Framework 4 jest całkowicie niezależna od Twoją decyzję, aby przejść do WF4 (System.Activities.*) z WF3 (System.Workflow.\*). Ten temat zawiera łącza do wskazówek dotyczących migracji WF, który zawiera informacje o pracy z WF3 i WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Oficjalne dokumenty programu WF migracji i podręczniki  
 [Omówienie migracji WF](https://go.microsoft.com/fwlink/?LinkId=153873) temat zawiera ogólne omówienie relacji między strategie WF3 i WF4 i migracji. Pomocnik tematy przejść do określonych tematów.  
  
 [Omówienie migracji WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 W tym artykule opisano relację między WF3 i WF4 i opcje, które mają jako użytkownik lub potencjalne technologii przepływu pracy w .NET 4.  
  
 [Migracja programu WF: Najlepsze rozwiązania dotyczące projektowania WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 W tym artykule omówiono sposób projektowania WF3 artefaktów, dzięki czemu mogą zostać łatwo zmigrowane do WF4.  
  
 [Wskazówki dotyczące WF: reguły](https://go.microsoft.com/fwlink/?LinkId=153854)  
 W tym artykule omówiono sposób dostosowania związane z zasadami inwestować do przodu w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] rozwiązania.  
  
 [Wskazówki dotyczące WF: Automatu stanów](https://go.microsoft.com/fwlink/?LinkId=153855)  
 W tym artykule omówiono przepływ sterowania WF4 modelowania w przypadku braku działań automatu stanów.  
  
 Należy pamiętać, że te wskazówki dotyczą tylko projekty przepływu pracy, których platformą docelową jest program .NET Framework 4. Przepływy pracy automatu stanów zostały dodane w programie .NET 4.0.1 wraz z wydaniem platformy Update 1, a następnie zostały zawarte w ramach programu .NET Framework 4.5. Aby uzyskać więcej informacji na temat przepływów pracy automatu stanów na platformie .NET 4.0.1 — 4.0.3 i .NET Framework 4.5, zobacz [aktualizacji 4.0.1 funkcje platformy Microsoft .NET Framework 4](https://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) i [przepływów pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
 [WF Podręcznik migracji: Niestandardowe działania](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Zawiera instrukcje dotyczące zmieniania projektu WF3 niestandardowe działania w WF4 i przykłady.  
  
 [WF Podręcznik migracji: Zaawansowane niestandardowe działania programu](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Zawiera wskazówki dotyczące przeprojektowanie zaawansowane WF3 niestandardowych działań korzystających z kolejek WF3 i harmonogramu działania podrzędne jako WF4 działań niestandardowych.  
  
 [Podręcznik migracji WF: przepływów pracy](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Zawiera instrukcje dotyczące przeprojektowanie WF3 przepływów na WF4 i przykłady.  
  
 [WF Podręcznik migracji: Hostowanie przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Zawiera wskazówki dotyczące zmieniania projektu WF3 kod hostingu jako kod hostingu WF4. Celem jest zapewnienie obejmują podstawowe różnice w hostowania między WF3 i WF4 przepływu pracy.  
  
 [WF Podręcznik migracji: Śledzenie przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Zawiera wskazówki dotyczące zmieniania projektu WF3 śledzenie kodu i konfiguracji za pomocą równoważnej WF4 śledzenie kodu i konfiguracji.  
  
 [WF wskazówek: Usługi przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Udostępnia zorientowane na przykład krok po kroku dotyczące zmieniania projektu przepływów pracy, które implementują Windows Communication Foundation (WCF) usługi sieci web (powszechnie znane jako usługi przepływu pracy) utworzone w WF3 na potrzeby WF4, typowe scenariusze dotyczące out-of-box działania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.Interop>
