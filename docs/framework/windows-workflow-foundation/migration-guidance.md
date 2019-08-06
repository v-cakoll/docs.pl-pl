---
title: Wskazówki dotyczące migracji
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 45f81b29f63701f690e396de2e9834f9933fd775
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796804"
---
# <a name="migration-guidance"></a>Wskazówki dotyczące migracji
[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]W systemie firma Microsoft udostępnia drugą wersję główną Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)]wydano w programie WinFX (obejmuje to typy w przestrzeni nazw System. Workflow\* . Namespaces, teraz nazywane WF3) i udoskonalone [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]w programie. WF3 jest również częścią programu [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale istnieje tam, gdzie występuje w nowej technologii przepływu pracy (typy w System. Activities\* . przestrzenie nazw; określane jako WF4). Biorąc pod uwagę, kiedy należy wdrożyć WF4, ważne jest, aby najpierw rozpoznać, czy należy kontrolować czas.  
  
- WF3 jest w pełni obsługiwaną częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
- Aplikacje WF3 są uruchamiane [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez modyfikacji i nadal są w pełni obsługiwane.  
  
- Można tworzyć nowe aplikacje WF3, a istniejące aplikacje można edytować w programie Visual Studio 2012 i są w pełni obsługiwane.  
  
 W związku z tym decyzja o przyjęciu .NET Framework 4 jest oddzielona od decyzji o przejściu do WF4 (System. Activities.\*) z WF3 (System. Workflow.\*). Ten temat zawiera linki do wskazówek dotyczących migracji programu WF, które zawierają informacje na temat pracy z WF3 i WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Oficjalne dokumenty dotyczące migracji WF i podręczniki  
 Temat [Omówienie migracji WF](https://go.microsoft.com/fwlink/?LinkId=153873) zawiera obszerne Omówienie relacji między WF3 i WF4 i strategiami migracji. Tematy pomocnicze przechodzenie do szczegółów określonych tematów.  
  
 [Omówienie migracji WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Opisuje relację między WF3 i WF4 i opcjami, które są dostępne jako użytkownik lub potencjalni użytkownicy technologii przepływu pracy w programie .NET 4.  
  
 [Migracja WF: Najlepsze rozwiązania dotyczące programowania WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 W tym artykule omówiono sposób projektowania artefaktów WF3, dzięki czemu można łatwiej migrować je do WF4.  
  
 [Wskazówki dotyczące WF: Przepisy](https://go.microsoft.com/fwlink/?LinkId=153854)  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] tym artykule omówiono sposób przenoszenia inwestycji związanych z regułami do rozwiązań.  
  
 [Wskazówki dotyczące WF: Automat Stanów](https://go.microsoft.com/fwlink/?LinkId=153855)  
 W tym artykule omówiono modelowanie przepływu sterowania WF4 w przypadku braku aktywności komputera stanu.  
  
 Należy zauważyć, że te wskazówki dotyczą tylko projektów przepływu pracy przeznaczonych dla .NET Framework 4. Przepływy pracy automatu Stanów zostały dodane w programie .NET 4.0.1 z wersją platformy Update 1 i zostały dołączone jako część .NET Framework 4,5. Aby uzyskać więcej informacji o przepływach pracy automatu stanów w oprogramowaniu .NET 4.0.1-4.0.3 i .NET Framework 4,5, zobacz temat [Update 4.0.1 for Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) i [przepływy pracy automatu Stanów](state-machine-workflows.md).  
  
 [Cookbook migracji WF: Działania niestandardowe](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Zawiera przykłady i instrukcje dotyczące ponownego projektowania działań niestandardowych WF3 na WF4.  
  
 [Cookbook migracji WF: Zaawansowane działania niestandardowe](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Zawiera wskazówki dotyczące ponownego projektowania zaawansowanych działań WF3, które korzystają z kolejek WF3 i planowania działań podrzędnych jako WF4 działań niestandardowych.  
  
 [Cookbook migracji WF: Przebieg](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Zawiera przykłady i instrukcje dotyczące przeprojektowania przepływów pracy WF3 na WF4.  
  
 [Cookbook migracji WF: Hosting przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Zawiera wskazówki dotyczące przeprojektowania kodu hostingu WF3 jako WF4 kodu hostingu. Celem jest pokrycie najważniejszych różnic między WF3 i WF4.  
  
 [Cookbook migracji WF: Śledzenie przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Zawiera wskazówki dotyczące przeprojektowania kodu śledzenia WF3 i konfiguracji przy użyciu równoważnego kodu śledzenia WF4 i konfiguracji.  
  
 [Wskazówki dotyczące WF: Usługi przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Zawiera przykładowe instrukcje krok po kroku dotyczące przeprojektowania przepływów pracy, które implementują usługi sieci Web programu Windows Communication Foundation (WCF), które są tworzone w WF3, aby używać WF4, dla typowych scenariuszy dla gotowych demonstracj.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.Interop>
