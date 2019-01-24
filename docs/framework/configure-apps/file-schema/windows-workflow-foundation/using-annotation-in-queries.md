---
title: Używanie adnotacji w zapytaniach
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 03951a374d81f53953fffad41c321470739cdcf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720304"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="d84a8-102">Używanie adnotacji w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="d84a8-102">Using Annotation in Queries</span></span>
<span data-ttu-id="d84a8-103">Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d84a8-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="d84a8-104">Na przykład może być kilka rekordów śledzenia na kilka przepływy pracy służące do być oznakowane za pomocą "Serwer poczty" == "Serwer1 poczty".</span><span class="sxs-lookup"><span data-stu-id="d84a8-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="d84a8-105">To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.</span><span class="sxs-lookup"><span data-stu-id="d84a8-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="d84a8-106">Dodawanie adnotacji</span><span class="sxs-lookup"><span data-stu-id="d84a8-106">Adding Annotations</span></span>  
 <span data-ttu-id="d84a8-107">Adnotację można dodać do zapytania śledzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d84a8-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d84a8-108">Te elementy zapytania śledzenia może służyć do tworzenia profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d84a8-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="d84a8-109">Można utworzyć profil śledzenia w konfiguracji lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="d84a8-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84a8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d84a8-110">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="d84a8-111">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="d84a8-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)
- [<span data-ttu-id="d84a8-112">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d84a8-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d84a8-113">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d84a8-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
