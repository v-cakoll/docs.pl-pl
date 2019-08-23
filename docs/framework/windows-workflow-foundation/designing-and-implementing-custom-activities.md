---
title: Projektowanie i implementowanie niestandardowych działań
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: b0d04572c65fd4e3e0ae96241217c9ae9aa0e2c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915361"
---
# <a name="designing-and-implementing-custom-activities"></a>Projektowanie i implementowanie niestandardowych działań
Działania niestandardowe w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] programie są tworzone przez umieszczenie działań dostarczonych przez system w działaniach złożonych lub przez utworzenie nowych typów, które pochodzą <xref:System.Activities.CodeActivity>z <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>. W tej sekcji opisano sposób tworzenia działań niestandardowych przy użyciu dowolnej metody.  
  
> [!IMPORTANT]
> Działania niestandardowe domyślnie są wyświetlane w Projektancie przepływu pracy jako prosty prostokąt z nazwą działania. Aby zapewnić niestandardową reprezentację działania w Projektancie przepływów pracy, należy również utworzyć projektanta niestandardowego. Aby uzyskać więcej informacji, zobacz [Używanie niestandardowych projektantów i szablonów działań](using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opcje tworzenia działań](activity-authoring-options-in-wf.md)  
 Omówienie stylów tworzenia dostępnych w programie [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].  
  
 [Używanie niestandardowego działania](using-a-custom-activity.md)  
 Opisuje sposób dodawania niestandardowego działania do projektu przepływu pracy.  
  
  [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md)  
 Opisuje sposób tworzenia działań asynchronicznych.  
  
 [Konfigurowanie walidacji działania](configuring-activity-validation.md)  
 Opisuje, w jaki sposób Walidacja działania może służyć do identyfikowania i zgłaszania błędów w konfiguracji działania przed jej wykonaniem.  
  
 [Tworzenie działania w środowisku uruchomieniowym](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 W tym artykule omówiono sposób tworzenia działań w <xref:System.Activities.DynamicActivity>czasie wykonywania przy użyciu programu.  
  
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
