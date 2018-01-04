---
title: "Projektowanie i implementowanie niestandardowych działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d162635a82027d1aaa46545dabad3e103d0f339c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="designing-and-implementing-custom-activities"></a>Projektowanie i implementowanie niestandardowych działań
Niestandardowe działania w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] są tworzone przez albo montaż działania dostarczane przez system do działań złożonych lub tworząc nowe typy, które pochodzą z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>. W tej sekcji opisano sposób tworzenia działań niestandardowych z jednej z metod.  
  
> [!IMPORTANT]
>  Działania niestandardowe, które domyślnie są wyświetlane w Projektancie przepływów pracy jako prosty prostokąt o nazwie działania. Zapewnienie niestandardowych wizualną reprezentację działanie w przepływie pracy projektanta należy również utworzyć designer niestandardowych. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Przy użyciu projektantów działań niestandardowych i szablonów](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opcje tworzenia działań](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 W tym artykule omówiono tworzenia style dostępne w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].  
  
 [Używanie niestandardowego działania](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 Opisuje sposób dodawania działań niestandardowych do projektu przepływu pracy.  
  
  [Tworzenie działań asynchronicznych](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 Opisuje sposób tworzenia działań asynchronicznego.  
  
 [Konfigurowanie walidacji działania](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 Opisuje sposób sprawdzania poprawności działania może służyć do identyfikowania i raportowania błędów konfiguracji działania przed jego wykonywania.  
  
 [Tworzenie działania w środowisku uruchomieniowym](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 W tym artykule omówiono sposób tworzenia działań w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity>.  
  
 [Właściwości wykonania przepływu pracy](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 Opisuje, jak dodać właściwości specyficzne dla kontekstu środowiska działania za pomocą właściwości wykonania przepływu pracy  
  
 [Używanie delegatów działania](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 Zawiera omówienie sposobu tworzenia i używania działań, które zawierają działanie delegatów.  
  
 [Lokalizacja działania](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 Informacje dotyczące używania lokalizacji zasobów ciągu w działaniach.  
  
 [Używanie rozszerzeń działania](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 Zawiera opis sposobu tworzenia i używania działania rozszerzeń.  
  
 [Wykorzystywanie źródeł strumieniowych danych OData z przepływu pracy](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 W tym artykule opisano kilka metod wywoływania usługi danych WCF z przepływu pracy.  
  
 [Wyznaczanie zakresu i widoczność definicji działania](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 Opisuje opcje i reguł określających widoczność zakresu i element członkowski danych działań.
