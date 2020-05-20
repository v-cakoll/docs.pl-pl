---
title: Podstawowe pojęcia związane z programem Windows Workflow
description: W tym artykule opisano niektóre koncepcje tworzenia przepływu pracy w .NET Framework 4.6.1, które mogą być nieznane dla niektórych deweloperów.
ms.date: 03/30/2017
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
ms.openlocfilehash: 07498241280191fb62a35a559a3391f7148c05b9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419892"
---
# <a name="fundamental-windows-workflow-concepts"></a>Podstawowe pojęcia związane z programem Windows Workflow
Tworzenie przepływów pracy w programie obejmuje [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] koncepcje, które mogą być nowe dla niektórych deweloperów. W tym temacie opisano niektóre koncepcje i sposób ich implementacji.  
  
## <a name="workflows-and-activities"></a>Przepływy pracy i działania  
 Przepływ pracy to strukturalna kolekcja akcji, które modelują proces. Każda akcja w przepływie pracy jest modelowana jako działanie. Host współdziała z przepływem pracy przy użyciu <xref:System.Activities.WorkflowInvoker> do wywoływania przepływu pracy tak, jakby był to metoda, <xref:System.Activities.WorkflowApplication> dla jawnej kontroli nad wykonywaniem pojedynczego wystąpienia przepływu pracy oraz <xref:System.ServiceModel.WorkflowServiceHost> dla interakcji opartych na komunikatach w scenariuszach obejmujących wiele wystąpień. Ze względu na to, że kroki przepływu pracy są zdefiniowane jako hierarchia działań, w celu zdefiniowania samego przepływu pracy można określić działanie najwyższego poziomu w hierarchii. Ten model hierarchii uwzględnia miejsce jawne `SequentialWorkflow` i `StateMachineWorkflow` klasy z poprzednich wersji. Same działania są opracowywane jako kolekcje innych działań (przy użyciu <xref:System.Activities.Activity> klasy jako bazy, zazwyczaj zdefiniowanej przy użyciu języka XAML) lub są niestandardowe utworzone przy użyciu <xref:System.Activities.CodeActivity> klasy, która może używać środowiska uruchomieniowego na potrzeby dostępu do danych lub przy użyciu <xref:System.Activities.NativeActivity> klasy, która udostępnia szerokość środowiska uruchomieniowego przepływu pracy do autora działania. Działania opracowane przy użyciu <xref:System.Activities.CodeActivity> i <xref:System.Activities.NativeActivity> są tworzone przy użyciu języków zgodnych ze standardem CLR, takich jak C#.  
  
## <a name="activity-data-model"></a>Model danych działań  
 Działania przechowują i udostępniają dane przy użyciu typów pokazanych w poniższej tabeli.  
  
|||  
|-|-|  
|Zmienna|Przechowuje dane w działaniu.|  
|Argument|Przenosi dane do działania i z niego.|  
|Wyrażenie|Działanie z wartością zwracaną z podwyższonym poziomem uprawnień użytą w powiązaniach argumentów.|  
  
## <a name="workflow-runtime"></a>Środowisko uruchomieniowe przepływu pracy  
 Środowisko uruchomieniowe przepływu pracy jest środowiskiem, w którym są wykonywane przepływy pracy. <xref:System.Activities.WorkflowInvoker>to najprostszy sposób wykonywania przepływu pracy. Na hoście są stosowane <xref:System.Activities.WorkflowInvoker> następujące elementy:  
  
- Aby synchronicznie wywołać przepływ pracy.  
  
- Aby zapewnić dane wejściowe lub pobrać dane wyjściowe z przepływu pracy.  
  
- , Aby dodać rozszerzenia, które mają być używane przez działania.  
  
 <xref:System.Activities.ActivityInstance>to bezpieczny dla wątków serwer proxy, którego hosty mogą używać do współdziałania z środowiskiem uruchomieniowym. Na hoście są stosowane <xref:System.Activities.ActivityInstance> następujące elementy:  
  
- Aby uzyskać wystąpienie, tworząc je lub ładując z magazynu wystąpień.  
  
- Aby otrzymywać powiadomienia o zdarzeniach cyklu życia wystąpienia.  
  
- Do kontrolowania wykonywania przepływu pracy.  
  
- Aby zapewnić dane wejściowe lub pobrać dane wyjściowe z przepływu pracy.  
  
- Aby sygnalizować kontynuację przepływu pracy i przekazać wartości do przepływu pracy.  
  
- Aby zachować dane przepływu pracy.  
  
- , Aby dodać rozszerzenia, które mają być używane przez działania.  
  
 Działania uzyskują dostęp do środowiska uruchomieniowego przepływu pracy przy użyciu odpowiedniej <xref:System.Activities.ActivityContext> klasy pochodnej, takiej jak <xref:System.Activities.NativeActivityContext> lub <xref:System.Activities.CodeActivityContext> . Służą one do rozpoznawania argumentów i zmiennych, do planowania działań podrzędnych i w wielu innych celach.  
  
## <a name="services"></a>Usługi  
 Przepływy pracy zapewniają naturalny sposób implementacji i uzyskiwania dostępu do luźno sprzężonych usług przy użyciu działań związanych z obsługą wiadomości. Działania związane z obsługą komunikatów są oparte na programie WCF i są podstawowym mechanizmem służącym do pobierania danych do i z przepływu pracy. Możesz redagować działania związane z obsługą wiadomości, aby modelować dowolny rodzaj niepotrzebnego wzorca wymiany komunikatów. Aby uzyskać więcej informacji, zobacz [działania dotyczące komunikatów](../wcf/feature-details/messaging-activities.md). Usługi przepływu pracy są hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy. Aby uzyskać więcej informacji, zobacz [hostowanie usług przepływu pracy — Omówienie](../wcf/feature-details/hosting-workflow-services-overview.md). Aby uzyskać więcej informacji na temat usług przepływu pracy, zobacz [usługi przepływu pracy](../wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Trwałość, wyładowywanie i długotrwałe przepływy pracy  
 Przepływ pracy systemu Windows upraszcza tworzenie długotrwałych, nieaktywnych programów, zapewniając:  
  
- Działania, które uzyskują dostęp do zewnętrznych danych wejściowych.  
  
- Możliwość tworzenia <xref:System.Activities.Bookmark> obiektów, które mogą być wznowione przez odbiornik hosta.  
  
- Możliwość utrwalania danych przepływu pracy i zwalniania przepływu pracy, a następnie ponownego załadowania i ponownego uaktywniania przepływu pracy w odpowiedzi na wznowienie <xref:System.Activities.Bookmark> obiektów w określonym przepływie pracy.  
  
 Przepływ pracy ciągle wykonuje działania do momentu, gdy nie będzie więcej działań do wykonania lub dopóki wszystkie aktualnie wykonywane działania nie oczekują na dane wejściowe. W tym ostatnim stanie przepływ pracy jest bezczynny. Host może zwolnić przepływy pracy, które zostały przetworzone bezczynnie i ponownie załadować je, aby kontynuować wykonywanie po nadejściu wiadomości. <xref:System.ServiceModel.Activities.WorkflowServiceHost>oferuje funkcje tej funkcji i zawiera rozszerzalne zasady zwalniania. Dla bloków wykonywania, które korzystają z danych o stanie volatile lub innych danych, które nie mogą być utrwalane, działanie może wskazywać na hosta, który nie powinien być utrwalany przy użyciu <xref:System.Activities.NoPersistHandle> . Przepływ pracy może również jawnie utrwalać swoje dane na trwałym nośniku magazynu za pomocą <xref:System.Activities.Statements.Persist> działania.
