---
title: Projektowanie i implementowanie niestandardowych działań
description: Ten artykuł zawiera zasoby służące do tworzenia niestandardowych działań w programie Workflow Foundation przez tworzenie działań złożonych lub tworzenie nowych typów działań.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419996"
---
# <a name="designing-and-implementing-custom-activities"></a>Projektowanie i implementowanie niestandardowych działań
Działania niestandardowe w programie [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] są tworzone przez umieszczenie działań dostarczonych przez system w działaniach złożonych lub przez utworzenie nowych typów, które pochodzą z <xref:System.Activities.CodeActivity> , <xref:System.Activities.AsyncCodeActivity> lub <xref:System.Activities.NativeActivity> . W tej sekcji opisano sposób tworzenia działań niestandardowych przy użyciu dowolnej metody.  
  
> [!IMPORTANT]
> Działania niestandardowe domyślnie są wyświetlane w Projektancie przepływu pracy jako prosty prostokąt z nazwą działania. Aby zapewnić niestandardową reprezentację działania w Projektancie przepływów pracy, należy również utworzyć projektanta niestandardowego. Aby uzyskać więcej informacji, zobacz [Używanie niestandardowych projektantów i szablonów działań](using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opcje tworzenia działań](activity-authoring-options-in-wf.md)  
 Omówienie stylów tworzenia dostępnych w programie [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .  
  
 [Używanie niestandardowego działania](using-a-custom-activity.md)  
 Opisuje sposób dodawania niestandardowego działania do projektu przepływu pracy.  
  
  [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md)  
 Opisuje sposób tworzenia działań asynchronicznych.  
  
 [Konfigurowanie walidacji działania](configuring-activity-validation.md)  
 Opisuje, w jaki sposób Walidacja działania może służyć do identyfikowania i zgłaszania błędów w konfiguracji działania przed jej wykonaniem.  
  
 [Tworzenie działania w środowisku uruchomieniowym](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 W tym artykule omówiono sposób tworzenia działań w czasie wykonywania przy użyciu programu <xref:System.Activities.DynamicActivity> .  
  
 [Właściwości wykonania przepływu pracy](workflow-execution-properties.md)  
 Opisuje sposób używania właściwości wykonywania przepływu pracy w celu dodawania właściwości specyficznych dla kontekstu do środowiska działania  
  
 [Używanie delegatów działania](using-activity-delegates.md)  
 W tym artykule omówiono sposób tworzenia i używania działań zawierających delegatów działań.
  
 [Używanie rozszerzeń działania](using-activity-extensions.md)  
 Opisuje sposób tworzenia i używania rozszerzeń działań.  
  
 [Wykorzystywanie źródeł strumieniowych danych OData z przepływu pracy](consuming-odata-feeds-from-a-workflow.md)  
 Opisuje kilka metod wywoływania usługi danych programu WCF z przepływu pracy.  
  
 [Wyznaczanie zakresu i widoczność definicji działania](activity-definition-scoping-and-visibility.md)  
 Opisuje opcje i reguły definiowania określania zakresu danych i widoczności elementów członkowskich dla działań.
