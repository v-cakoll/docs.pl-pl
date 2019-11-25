---
title: Wskazówki dotyczące migracji
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 8abc241331b3d322763ffd67b41ff676ebc680fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283202"
---
# <a name="migration-guidance"></a>Wskazówki dotyczące migracji

W .NET Framework 4 firma Microsoft udostępnia drugą wersję główną Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] został wydano w usłudze WinFX (w tym w przestrzeniach nazw System. Workflow.\*, nazywana jako WF3) i ulepszona w .NET Framework 3,5. WF3 jest również częścią .NET Framework 4, ale istnieje tam, gdzie jest to nowa technologia przepływu pracy (typy w przestrzeni nazw System. Activities.\*; określane jako WF4). Biorąc pod uwagę, kiedy należy wdrożyć WF4, ważne jest, aby najpierw rozpoznać, czy należy kontrolować czas.  
  
- WF3 jest w pełni obsługiwaną częścią .NET Framework 4.  
  
- Aplikacje WF3 są uruchamiane na .NET Framework 4 bez modyfikacji i nadal będą w pełni obsługiwane.  
  
- Można tworzyć nowe aplikacje WF3, a istniejące aplikacje można edytować w programie Visual Studio 2012 i są w pełni obsługiwane.  
  
 W związku z tym decyzja o przyjęciu .NET Framework 4 jest oddzielona od decyzji o przejściu do WF4 (System. Activities.\*) z WF3 (System. Workflow.\*). Ten temat zawiera linki do wskazówek dotyczących migracji programu WF, które zawierają informacje na temat pracy z WF3 i WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Oficjalne dokumenty dotyczące migracji WF i podręczniki  
 Temat [Omówienie migracji WF](https://go.microsoft.com/fwlink/?LinkId=153873) zawiera obszerne Omówienie relacji między WF3 i WF4 i strategiami migracji. Tematy pomocnicze przechodzenie do szczegółów określonych tematów.  
  
 [Omówienie migracji WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Opisuje relację między WF3 i WF4 i opcjami, które są dostępne jako użytkownik lub potencjalni użytkownicy technologii przepływu pracy w programie .NET 4.  
  
 [Migracja WF: najlepsze rozwiązania dotyczące programowania WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 W tym artykule omówiono sposób projektowania artefaktów WF3, dzięki czemu można łatwiej migrować je do WF4.  
  
 [Wskazówki dotyczące WF: reguły](https://go.microsoft.com/fwlink/?LinkId=153854)  
 W tym artykule omówiono sposób przenoszenia inwestycji związanych z regułami do .NET Framework 4 rozwiązań.  
  
 [Wskazówki dotyczące WF: automat Stanów](https://go.microsoft.com/fwlink/?LinkId=153855)  
 W tym artykule omówiono modelowanie przepływu sterowania WF4 w przypadku braku aktywności komputera stanu.  
  
 Należy zauważyć, że te wskazówki dotyczą tylko projektów przepływu pracy przeznaczonych dla .NET Framework 4. Przepływy pracy automatu Stanów zostały dodane w programie .NET 4.0.1 z wersją platformy Update 1 i zostały dołączone jako część .NET Framework 4,5. Aby uzyskać więcej informacji o przepływach pracy automatu stanów w oprogramowaniu .NET 4.0.1-4.0.3 i .NET Framework 4,5, zobacz temat [Update 4.0.1 for Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) i [przepływy pracy automatu Stanów](state-machine-workflows.md).  
  
 [Cookbook migracji WF: działania niestandardowe](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Zawiera przykłady i instrukcje dotyczące ponownego projektowania działań niestandardowych WF3 na WF4.  
  
 [Cookbook migracji WF: Zaawansowane działania niestandardowe](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Zawiera wskazówki dotyczące ponownego projektowania zaawansowanych działań WF3, które korzystają z kolejek WF3 i planowania działań podrzędnych jako WF4 działań niestandardowych.  
  
 [Cookbook migracji WF: przepływy pracy](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Zawiera przykłady i instrukcje dotyczące przeprojektowania przepływów pracy WF3 na WF4.  
  
 [Cookbook migracji WF: hosting przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Zawiera wskazówki dotyczące przeprojektowania kodu hostingu WF3 jako WF4 kodu hostingu. Celem jest pokrycie najważniejszych różnic między WF3 i WF4.  
  
 [Cookbook migracji WF: śledzenie przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Zawiera wskazówki dotyczące przeprojektowania kodu śledzenia WF3 i konfiguracji przy użyciu równoważnego kodu śledzenia WF4 i konfiguracji.  
  
 [Wskazówki dotyczące WF: usługi przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Zawiera przykładowe instrukcje krok po kroku dotyczące przeprojektowania przepływów pracy, które implementują usługi sieci Web programu Windows Communication Foundation (WCF), które są tworzone w WF3, aby używać WF4, dla typowych scenariuszy dla gotowych demonstracj.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.Interop>
