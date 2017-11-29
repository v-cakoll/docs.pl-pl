---
title: "Wybierz działanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a76b666dde6674740790c161753570193912afd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pick-activity"></a><span data-ttu-id="aa285-102">Wybierz działanie</span><span class="sxs-lookup"><span data-stu-id="aa285-102">Pick Activity</span></span>
<span data-ttu-id="aa285-103"><xref:System.Activities.Statements.Pick> Działania upraszcza modelowania zestawu wyzwalaczy zdarzeń oraz ich odpowiednich programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="aa285-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="aa285-104">A <xref:System.Activities.Statements.Pick> działania zawiera kolekcję <xref:System.Activities.Statements.PickBranch> działań, gdzie każdy <xref:System.Activities.Statements.PickBranch> jest parowanie między <xref:System.Activities.Statements.PickBranch.Trigger%2A> działania i <xref:System.Activities.Statements.PickBranch.Action%2A> działania.</span><span class="sxs-lookup"><span data-stu-id="aa285-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="aa285-105">W czasie wykonywania Wyzwalacze dla wszystkie gałęzie są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="aa285-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="aa285-106">Po zakończeniu jednego wyzwalacza, następnie wykonywane jest jego działanie, a wszystkie inne wyzwalacze zostały anulowane.</span><span class="sxs-lookup"><span data-stu-id="aa285-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="aa285-107">Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działanie przypomina [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="aa285-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="aa285-108">Poniższy zrzut ekranu z [za pomocą działania wybierz](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) przykład zestawu SDK zawiera czynności pobrania z dwóch gałęziach.</span><span class="sxs-lookup"><span data-stu-id="aa285-108">The following screenshot from the [Using the Pick Activity](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="aa285-109">Jedna gałąź ma wyzwalacz o nazwie **odczytu danych wejściowych**, niestandardowe działanie, które odczytuje dane wejściowe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="aa285-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="aa285-110">Drugi gałęzi ma <xref:System.Activities.Statements.Delay> działania wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="aa285-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="aa285-111">Jeśli **odczytu danych wejściowych** działania odbiera dane przed <xref:System.Activities.Statements.Delay> zakończenie działania <xref:System.Activities.Statements.Delay> opóźnienie zostanie anulowane i powitanie zostanie wyświetlony w konsoli.</span><span class="sxs-lookup"><span data-stu-id="aa285-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="aa285-112">W przeciwnym razie, jeśli **odczytu danych wejściowych** działania nie odbiera danych w wyznaczonym czasie, a następnie zostanie anulowane i komunikat o limicie czasu zostanie wyświetlony w konsoli.</span><span class="sxs-lookup"><span data-stu-id="aa285-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="aa285-113">Jest to wspólnego wzorca użyte do dodania do dowolnej akcji przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="aa285-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 <span data-ttu-id="aa285-114">![Wybierz działanie](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span><span class="sxs-lookup"><span data-stu-id="aa285-114">![Pick Activity](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="aa285-115">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="aa285-115">Best practices</span></span>  
 <span data-ttu-id="aa285-116">Używając pobrania gałęzi, która wykonuje jest gałęzi, w której wyzwalacz zakończeniu najpierw.</span><span class="sxs-lookup"><span data-stu-id="aa285-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="aa285-117">Koncepcyjnie wyzwalacze wszystkie wykonywane równolegle, a jeden wyzwalacz mogło zostać wykonane większość swojej logiki przed została anulowana po zakończeniu innego wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="aa285-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="aa285-118">Pamiętając o tym ogólne wytyczne do wykonania w przypadku używania działania pobrania jest zaliczenie wyzwalacza reprezentujący pojedyncze zdarzenie i poddane jako ilością logiki możliwie go.</span><span class="sxs-lookup"><span data-stu-id="aa285-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="aa285-119">Najlepiej, jeśli wyzwalacz powinien zawierać wystarczającego logikę do odbierania zdarzeń i przetwarzania zdarzenia należy przejść do akcji gałęzi.</span><span class="sxs-lookup"><span data-stu-id="aa285-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="aa285-120">Ta metoda pozwala zmniejszyć nakładania się wykonanie wyzwalacze.</span><span class="sxs-lookup"><span data-stu-id="aa285-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="aa285-121">Rozważmy na przykład <xref:System.Activities.Statements.Pick> z dwóch wyzwalaczy, w którym każdy wyzwalacz zawiera <xref:System.ServiceModel.Activities.Receive> działania następuje dodatkową logikę.</span><span class="sxs-lookup"><span data-stu-id="aa285-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="aa285-122">Jeśli dodatkową logikę wprowadza bezczynności punkt, istnieje możliwość zarówno <xref:System.ServiceModel.Activities.Receive> pomyślne zakończenie działania.</span><span class="sxs-lookup"><span data-stu-id="aa285-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="aa285-123">Jeden wyzwalacz zostanie w pełni ukończone podczas będzie inny częściowo ukończone.</span><span class="sxs-lookup"><span data-stu-id="aa285-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="aa285-124">W niektórych scenariuszach jest nie do przyjęcia akceptowanie komunikatu i częściowo ukończenia przetwarzania go.</span><span class="sxs-lookup"><span data-stu-id="aa285-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="aa285-125">W związku z tym gdy przy użyciu działań WF wbudowanych obsługi wiadomości, takich jak <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>, podczas <xref:System.ServiceModel.Activities.Receive> jest często używana w wyzwalacza, <xref:System.ServiceModel.Activities.SendReply> i innych logiki należy umieścić w akcji, o ile to możliwe.</span><span class="sxs-lookup"><span data-stu-id="aa285-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="aa285-126">Za pomocą działania pobranie w Projektancie</span><span class="sxs-lookup"><span data-stu-id="aa285-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="aa285-127">Aby użyć pobrania w projektancie, Znajdź **wybierz** i **PickBranch** w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="aa285-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="aa285-128">Przeciągnij i upuść **wybierz** na kanwę.</span><span class="sxs-lookup"><span data-stu-id="aa285-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="aa285-129">Domyślnie nowy **wybierz** działania w Projektancie będzie zawierać dwóch gałęziach.</span><span class="sxs-lookup"><span data-stu-id="aa285-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="aa285-130">Aby dodać dodatkowe gałęzie, przeciągnij **PickBranch** działania i upuść go obok istniejących gałęzi.</span><span class="sxs-lookup"><span data-stu-id="aa285-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="aa285-131">Działania mogą być upuszczone na **wybierz** działania w jednej **wyzwalacza** obszaru lub **akcji** obszaru dowolnego **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="aa285-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="aa285-132">Za pomocą działania pobrania w kodzie</span><span class="sxs-lookup"><span data-stu-id="aa285-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="aa285-133"><xref:System.Activities.Statements.Pick> Działania jest używana przez wypełnianie jej <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji z <xref:System.Activities.Statements.PickBranch> działań.</span><span class="sxs-lookup"><span data-stu-id="aa285-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="aa285-134"><xref:System.Activities.Statements.PickBranch> Działania każdego mają <xref:System.Activities.Statements.PickBranch.Trigger%2A> właściwości typu <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="aa285-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="aa285-135">Po ukończeniu określonego działania wykonywania, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.</span><span class="sxs-lookup"><span data-stu-id="aa285-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="aa285-136">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Activities.Statements.Pick> działanie, aby zaimplementować przekroczenie limitu czasu dla działania odczytuje wiersz z konsoli.</span><span class="sxs-lookup"><span data-stu-id="aa285-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
