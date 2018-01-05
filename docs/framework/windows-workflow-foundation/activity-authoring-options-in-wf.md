---
title: "Opcje tworzenia działania WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0422b7b433c8c2a6889e00d559207d25ed42eff1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="activity-authoring-options-in-wf"></a>Opcje tworzenia działania WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]zapewnia kilka opcji tworzenia działań niestandardowych. Poprawną metodę do użycia na potrzeby tworzenia dane działanie zależy od tego, jakie funkcje środowiska wykonawczego są wymagane.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Przy wyborze klasy podstawowej działanie (Activity) do użycia na potrzeby tworzenia działań niestandardowych  
 W poniższej tabeli wymieniono funkcje dostępne w klasach podstawowych działań niestandardowych.  
  
|Klasa podstawowego elementu activity|Funkcje dostępne|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Redaguj grup dostarczane przez system i niestandardowych działań do działania złożonego.|  
|<xref:System.Activities.CodeActivity>|Implementuje funkcje imperatywnych zapewniając <xref:System.Activities.CodeActivity%601.Execute%2A> metodę, która może zostać zastąpiona. Umożliwia również dostęp do śledzenia, zmienne i argumenty.|  
|<xref:System.Activities.NativeActivity>|Zawiera wszystkie funkcje <xref:System.Activities.CodeActivity>, oraz Przerywanie wykonywania działań, anulowanie wykonywania działań podrzędnych korzystanie z zakładek i planowania działań, działanie akcje i funkcje.|  
|<xref:System.Activities.DynamicActivity>|Zapewnia to podejście DOM podobne do tworzenia działań, które interfejsy projektanta WF i maszyny czasu wykonywania za pośrednictwem <!--zz <xref:System.ComponentModel.IcustomTypeDescriptor>--> `IcustomTypeDescriptor`, dzięki czemu nowe działania, które ma zostać utworzony bez zdefiniowania nowych typów.|  
  
## <a name="authoring-activities-using-activity"></a>Czynności tworzenia pakietów administracyjnych, korzystając z działania  
 Działania, które pochodzą z <xref:System.Activities.Activity> tworzą funkcji przez łączenie innych istniejących działań. Te działania mogą być istniejących niestandardowe działania i działania z [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Biblioteka działań. Składanie te działania jest najprostszym sposobem tworzenia funkcji niestandardowych. Takie podejście jest najczęściej chroniła za pomocą środowiska projektowania visual dla przepływów pracy autorstwa.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Tworzenie przy użyciu klasy CodeActivity ani AsyncCodeActivity działania  
 Działania, które pochodzą z <xref:System.Activities.CodeActivity> lub <xref:System.Activities.AsyncCodeActivity> można zaimplementować ważnych funkcji przez zastąpienie <xref:System.Activities.CodeActivity%601.Execute%2A> metody o niestandardowych kodów imperatywnych. Niestandardowy kod zostanie wykonany po wykonaniu działania w czasie wykonywania. Chociaż dostęp do funkcji niestandardowych działań utworzonych w ten sposób, ich nie mają dostęp do wszystkich funkcji środowiska uruchomieniowego, takie jak pełny dostęp do środowiska wykonawczego możliwość planować działań podrzędnych, tworzenia zakładek lub obsługę Anuluj lub metodę Abort. Gdy <xref:System.Activities.CodeActivity> wykonuje, ma dostęp do skrócona wersja środowiska wykonawczego (za pośrednictwem <xref:System.Activities.CodeActivityContext> lub <xref:System.Activities.AsyncCodeActivityContext> klasy). Działania utworzone przy użyciu <xref:System.Activities.CodeActivity> mają dostęp do rozpoznawania argumentów i zmienna, rozszerzenia i śledzenia. Planowanie asynchroniczne działania może odbywać się przy użyciu <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Tworzenie za pomocą działania NativeActivity działania  
 Działań, które pochodzą z <xref:System.Activities.NativeActivity>, podobne do tych, które pochodzą z <xref:System.Activities.CodeActivity>, utworzenia ważnych funkcji przez zastąpienie <xref:System.Activities.NativeActivity.Execute%2A>, ale mają także dostęp do wszystkich funkcji środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> który pobiera przekazany <xref:System.Activities.NativeActivity.Execute%2A> metody. Ten kontekst został obsługę planowania i anulowania działania podrzędne, wykonywania <xref:System.Activities.ActivityAction> i <!--zz <xref:System.Activities.ActivityFunc>--> `ActivityFunc` obiektów, transakcje przechodzenia w przepływie pracy, wywołania asynchronicznego procesów, anulowanie i Trwa przerywanie wykonywania, dostęp do właściwości wykonania i rozszerzenia i zakładek (dojść do wznawiania przepływów pracy wstrzymana).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Tworzenie przy użyciu DynamicActivity działania  
 W przeciwieństwie do innych trzy typy działań, nowych funkcji nie jest tworzony przez wyprowadzanie nowych typów z <xref:System.Activities.DynamicActivity> (klasa jest zapieczętowany), ale zamiast tego funkcji do zebrania <xref:System.Activities.DynamicActivity.Properties%2A> i <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości za pomocą dokumentu działania Obiekt modelu (DOM).  
  
## <a name="authoring-activities-that-return-a-result"></a>Tworzenie działań, które zwracają wynik  
 Wiele działań musi zwracać wynik po ich wykonanie. Mimo że można zawsze zdefiniować niestandardowe <xref:System.Activities.OutArgument%601> w działaniu w tym celu, zalecane jest aby zamiast tego użyć <xref:System.Activities.Activity%601>, lub pochodzić od <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>. Każda z tych klas podstawowych ma <xref:System.Activities.OutArgument%601> o nazwie Result używanego przez działanie dla jej wartości zwracanej. Działania, które zwracają wynik powinien być używany tylko, jeśli tylko jeden wynik musi być zwracane z działania; Jeśli wiele wyników muszą zostać zwrócone, oddziel <xref:System.Activities.OutArgument%601> elementów członkowskich należy użyć.
