---
title: Pojęcia dotyczące przepływu pracy Windows podstawowe
ms.date: 03/30/2017
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
ms.openlocfilehash: ef2f327bdf2641648d266cecd0c6674762a95c18
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347828"
---
# <a name="fundamental-windows-workflow-concepts"></a>Pojęcia dotyczące przepływu pracy Windows podstawowe
Projektowanie przepływów pracy w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] korzysta z koncepcji, które mogą być nowe dla niektórych programistów. W tym temacie opisano niektóre z pojęć i ich implementacji.  
  
## <a name="workflows-and-activities"></a>Przepływy pracy i działania  
 Przepływ pracy jest strukturą kolekcję akcji, który modeluje procesu. Każdej akcji w przepływie pracy są modelowane jako działania. Host wchodzi w interakcję z przepływem pracy przy użyciu <xref:System.Activities.WorkflowInvoker> do wywoływania przepływu pracy, tak jakby był metodą, <xref:System.Activities.WorkflowApplication> dla jawną kontrolę nad wykonywaniem wystąpienia jeden przepływ pracy i <xref:System.ServiceModel.WorkflowServiceHost> oparta na komunikatach interakcji w wielu wystąpieniach scenariusze. Ponieważ kroki przepływu pracy są zdefiniowane jako hierarchię działań, działanie najwyższego poziomu w hierarchii można powiedzieć do definiowania samego przepływu pracy. Ten model hierarchii zajmuje miejsce jawne `SequentialWorkflow` i `StateMachineWorkflow` klasy z poprzedniej wersji. Działania, samodzielnie są tworzone jako kolekcje innych działań (przy użyciu <xref:System.Activities.Activity> klasy jako podstawa, zazwyczaj definiowane przy użyciu XAML) lub są tworzone za pomocą niestandardowego <xref:System.Activities.CodeActivity> klasy, która może korzystania ze środowiska uruchomieniowego, aby uzyskać dostęp do danych lub za pomocą <xref:System.Activities.NativeActivity> klasy, która przedstawia szerokość środowiska uruchomieniowego przepływu pracy do autora działania. Działania opracowane za pomocą <xref:System.Activities.CodeActivity> i <xref:System.Activities.NativeActivity> są tworzone przy użyciu zgodnych ze standardami CLR języków, takich jak C#.  
  
## <a name="activity-data-model"></a>Model danych aktywności  
 Działania przechowywania i udostępniania danych przy użyciu typów pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Zmienna|Przechowuje dane w działaniu.|  
|Argument|Przeniesienie danych do i z działania.|  
|Wyrażenie|Działanie z wartością zwracaną z podwyższonym poziomem uprawnień używać w powiązaniach argumentu.|  
  
## <a name="workflow-runtime"></a>Środowisko wykonawcze przepływów pracy  
 Środowisko wykonawcze przepływów pracy jest środowisko, w którym wykonania przepływów pracy. <xref:System.Activities.WorkflowInvoker> jest to najprostszy sposób na wykonanie przepływu pracy. Host używa <xref:System.Activities.WorkflowInvoker> dla następujących:  
  
-   Synchronicznego wywoływania przepływu pracy.  
  
-   Podaj dane wejściowe lub pobrać dane wyjściowe z przepływu pracy.  
  
-   Aby dodać rozszerzenia do użycia przez działania.  
  
 <xref:System.Activities.ActivityInstance> jest metodą o bezpiecznych wątkach serwerem proxy, który hostów może służyć do interakcji ze środowiskiem uruchomieniowym. Host używa <xref:System.Activities.ActivityInstance> dla następujących:  
  
-   Można uzyskać wystąpienie przez jej tworzenia lub załadowanie go ze sklepu wystąpienia.  
  
-   Aby otrzymywać powiadomienia o zdarzenia cyklu życia wystąpienia.  
  
-   Do kontrolowania wykonywania przepływu pracy.  
  
-   Podaj dane wejściowe lub pobrać dane wyjściowe z przepływu pracy.  
  
-   Sygnał kontynuacji przepływu pracy i wartości są przekazywane do przepływu pracy.  
  
-   Aby zachować dane przepływu pracy.  
  
-   Aby dodać rozszerzenia do użycia przez działania.  
  
 Działania uzyskać dostęp do środowiska wykonawczego przepływów pracy przy użyciu odpowiedniego <xref:System.Activities.ActivityContext> pochodne klasy, takie jak <xref:System.Activities.NativeActivityContext> lub <xref:System.Activities.CodeActivityContext>. Używają to postępowania po otrzymaniu zmienne i argumenty, planowanie działania podrzędne i do innych celów.  
  
## <a name="services"></a>Usługi  
 Przepływy pracy zawierają naturalny sposób wdrożenia i uzyskiwanie dostępu do usług luźno powiązane przy użyciu działań dotyczących komunikatów. Działań dotyczących komunikatów są oparte na WCF i są podstawowym mechanizmem stosowane w celu pobrania danych do i z przepływu pracy. Można utworzyć działań dotyczących komunikatów ze sobą, aby modelować dowolnego rodzaju wymiany komunikatów, którą chcesz. Aby uzyskać więcej informacji, zobacz [działań Messaging](../../../docs/framework/wcf/feature-details/messaging-activities.md). Usługi przepływu pracy są hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy. Aby uzyskać więcej informacji, zobacz [przegląd usług przepływu pracy obsługującego](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md). Aby uzyskać więcej informacji na temat usług przepływu pracy zobacz [usług przepływu pracy](../../../docs/framework/wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Stan trwały, zwalniania i długotrwałe przepływy pracy  
 Przepływ pracy Windows upraszcza tworzenie programów reaktywne długotrwałych, zapewniając:  
  
-   Działania, do których dostęp zewnętrznych danych wejściowych.  
  
-   Możliwość tworzenia <xref:System.Activities.Bookmark> obiektów, które może być wznowione przez odbiornik hosta.  
  
-   Zdolność do utrwalenia danych przepływu pracy i zwalnianie przepływu pracy, a następnie załaduj ponownie i Uaktywnij ponownie przepływu pracy w odpowiedzi na wznowienie <xref:System.Activities.Bookmark> obiektów w określonego przepływu pracy.  
  
 Przepływ pracy nieprzerwanie wykonuje działania, dopóki nie ma żadnych więcej działań do wykonania lub dopóki wszystkie aktualnie wykonywanego działania oczekiwania na dane wejściowe. W tym ostatnim stanie przepływu pracy jest w stanie bezczynności. Często hosta można zwolnić przepływów pracy, które przeszły bezczynności i ponownie załadować je, aby kontynuować wykonywanie, gdy wiadomość zostaje nadejściu. <xref:System.ServiceModel.Activities.WorkflowServiceHost> oferuje funkcję dla tej funkcji i udostępnia zasady rozszerzonego zwolnienia. Dla bloków wykonywania korzystające z danych o stanie lotnych lub inne dane, które nie może zostać utrwalona, działanie może wskazywać na hoście, nie należy go utrwalone przy użyciu <xref:System.Activities.NoPersistHandle>. Przepływu pracy można także jawnie utrwalić swoje dane do nośnika trwałego magazynu przy użyciu <xref:System.Activities.Statements.Persist> działania.
