---
title: Projektowanie i implementowanie niestandardowych działań
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 61a5de5a15835c728c18c0136952cf7ffdbaf000
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945850"
---
# <a name="designing-and-implementing-custom-activities"></a>Projektowanie i implementowanie niestandardowych działań
Niestandardowe działania w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] są tworzone przez albo montażu działania dostarczane przez system do działań złożonych lub tworząc nowe typy, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>. W tej sekcji opisano sposób tworzenia działań niestandardowych za pomocą jednej z metod.  
  
> [!IMPORTANT]
>  Działania niestandardowe, które domyślnie są wyświetlane w Projektancie przepływu pracy jako prosty prostokąt o nazwie tego działania. Zapewnienie niestandardowe wizualnej reprezentacji działania w przepływie pracy projektanta należy także utworzyć niestandardowego projektanta. Aby uzyskać więcej informacji, zobacz [szablonów i za pomocą projektantów działań niestandardowych](using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opcje tworzenia działań](activity-authoring-options-in-wf.md)  
 W tym artykule omówiono tworzenia style, dostępne w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].  
  
 [Używanie niestandardowego działania](using-a-custom-activity.md)  
 W tym artykule opisano sposób dodawania działań niestandardowych do projektu przepływu pracy.  
  
  [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md)  
 Opisuje sposób tworzenie działań asynchronicznych.  
  
 [Konfigurowanie walidacji działania](configuring-activity-validation.md)  
 Opisuje sposób sprawdzania poprawności działania może służyć do identyfikowania i raportowania błędów konfiguracji działanie przed jej wykonanie.  
  
 [Tworzenie działania w środowisku uruchomieniowym](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 W tym artykule omówiono sposób tworzenia działania w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity>.  
  
 [Właściwości wykonania przepływu pracy](workflow-execution-properties.md)  
 Opisuje sposób używania właściwości wykonania przepływu pracy, aby dodać określonej właściwości kontekstu do działania środowiska  
  
 [Używanie delegatów działania](using-activity-delegates.md)  
 W tym artykule omówiono sposób tworzenia i używania działań, które zawierają działania delegatach.
  
 [Używanie rozszerzeń działania](using-activity-extensions.md)  
 Opisuje sposób tworzenia i używania rozszerzeń działania.  
  
 [Wykorzystywanie źródeł strumieniowych danych OData z przepływu pracy](consuming-odata-feeds-from-a-workflow.md)  
 W tym artykule opisano kilka metod wywoływania usługi danych WCF z przepływu pracy.  
  
 [Wyznaczanie zakresu i widoczność definicji działania](activity-definition-scoping-and-visibility.md)  
 W tym artykule opisano opcje i reguł określających widoczność zakresu i element członkowski danych działań.
