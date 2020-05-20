---
title: Wybieranie działania
description: W programie Workflow Foundation działanie wybierz upraszcza modelowanie zestawu wyzwalaczy zdarzeń, a następnie odpowiadające im procedury obsługi.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: eb59dc20919ed2d30a48f920ad154d4b0d99c41f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421465"
---
# <a name="pick-activity"></a><span data-ttu-id="b844f-103">Wybieranie działania</span><span class="sxs-lookup"><span data-stu-id="b844f-103">Pick Activity</span></span>
<span data-ttu-id="b844f-104"><xref:System.Activities.Statements.Pick>Działanie upraszcza modelowanie zestawu wyzwalaczy zdarzeń, a następnie odpowiadające im procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="b844f-104">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="b844f-105"><xref:System.Activities.Statements.Pick>Działanie zawiera kolekcję <xref:System.Activities.Statements.PickBranch> działań, z których każda <xref:System.Activities.Statements.PickBranch> jest parą między <xref:System.Activities.Statements.PickBranch.Trigger%2A> działaniem a <xref:System.Activities.Statements.PickBranch.Action%2A> działaniem.</span><span class="sxs-lookup"><span data-stu-id="b844f-105">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="b844f-106">W czasie wykonywania wyzwalacze dla wszystkich rozgałęzień są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="b844f-106">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="b844f-107">Po zakończeniu jednego wyzwalacza odpowiednia akcja jest wykonywana i wszystkie pozostałe wyzwalacze są anulowane.</span><span class="sxs-lookup"><span data-stu-id="b844f-107">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="b844f-108">Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działania jest podobne do działania .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity> .</span><span class="sxs-lookup"><span data-stu-id="b844f-108">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="b844f-109">Na poniższym zrzucie ekranu z poziomu zestawu SDK [działania wybierz](./samples/using-the-pick-activity.md) zostanie wyświetlona czynność pobrania z dwoma gałęziami.</span><span class="sxs-lookup"><span data-stu-id="b844f-109">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="b844f-110">Jedna gałąź ma wyzwalacz o nazwie **Odczyt wejściowy**, działanie niestandardowe, które odczytuje dane wejściowe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b844f-110">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="b844f-111">Druga gałąź ma <xref:System.Activities.Statements.Delay> wyzwalacz aktywności.</span><span class="sxs-lookup"><span data-stu-id="b844f-111">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="b844f-112">Jeśli działanie **odczytu danych wejściowych** odbiera dane przed <xref:System.Activities.Statements.Delay> zakończeniem działania, <xref:System.Activities.Statements.Delay> opóźnienie zostanie anulowane, a powitanie zostanie zapisany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="b844f-112">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="b844f-113">W przeciwnym razie, jeśli działanie **Odczytaj dane wejściowe** nie odbiera danych w wyznaczonym czasie, zostanie anulowane, a w konsoli zostanie zapisany komunikat o limicie czasu.</span><span class="sxs-lookup"><span data-stu-id="b844f-113">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="b844f-114">Jest to typowy wzorzec służący do dodawania limitu czasu do dowolnej akcji.</span><span class="sxs-lookup"><span data-stu-id="b844f-114">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Wybieranie działania](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="b844f-116">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="b844f-116">Best practices</span></span>  
 <span data-ttu-id="b844f-117">W przypadku korzystania z funkcji wybierz gałąź, która jest wykonywana, jest gałęzią, której wyzwalacz zostaje zakończony jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="b844f-117">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="b844f-118">Koncepcyjnie wszystkie wyzwalacze są wykonywane równolegle, a jeden wyzwalacz może wykonać większość jego logiki przed anulowaniem przez zakończenie innego wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="b844f-118">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="b844f-119">Z tego względu ogólne wytyczne, które należy wykonać podczas korzystania z działania pobrania, to traktowanie wyzwalacza w postaci pojedynczego zdarzenia i umieszczenie jak najmniejszej logiki.</span><span class="sxs-lookup"><span data-stu-id="b844f-119">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="b844f-120">W idealnym przypadku wyzwalacz powinien zawierać tylko wystarczającą logikę, aby można było odebrać zdarzenie, a wszystkie przetwarzanie tego zdarzenia powinno nastąpić do działania gałęzi.</span><span class="sxs-lookup"><span data-stu-id="b844f-120">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="b844f-121">Ta metoda minimalizuje ilość nakładania się między wykonaniem wyzwalaczy.</span><span class="sxs-lookup"><span data-stu-id="b844f-121">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="b844f-122">Rozważmy na przykład <xref:System.Activities.Statements.Pick> z dwoma wyzwalaczami, gdzie każdy wyzwalacz zawiera <xref:System.ServiceModel.Activities.Receive> działanie, a następnie dodatkową logikę.</span><span class="sxs-lookup"><span data-stu-id="b844f-122">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="b844f-123">Jeśli dodatkowa logika wprowadza punkt bezczynności, istnieje możliwość, że obie <xref:System.ServiceModel.Activities.Receive> działania kończą się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b844f-123">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="b844f-124">Jeden wyzwalacz zostanie w pełni ukończony, podczas gdy inny zostanie częściowo ukończony.</span><span class="sxs-lookup"><span data-stu-id="b844f-124">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="b844f-125">W niektórych scenariuszach zaakceptowanie komunikatu, a następnie częściowe zakończenie jego przetwarzania jest nieakceptowalne.</span><span class="sxs-lookup"><span data-stu-id="b844f-125">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="b844f-126">W związku z tym, w przypadku korzystania z wbudowanych działań związanych z obsługą mechanizmu WF, takich jak <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> , gdy <xref:System.ServiceModel.Activities.Receive> jest często używany w wyzwalaczu, <xref:System.ServiceModel.Activities.SendReply> a w miarę możliwości należy umieścić w niej inną logikę.</span><span class="sxs-lookup"><span data-stu-id="b844f-126">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="b844f-127">Korzystanie z działania pobrania w projektancie</span><span class="sxs-lookup"><span data-stu-id="b844f-127">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="b844f-128">Aby użyć **funkcji wybierz w projektancie, Znajdź pozycję** find and **PickBranch** w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="b844f-128">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="b844f-129">Przeciągnij i upuść **wybór** na kanwie.</span><span class="sxs-lookup"><span data-stu-id="b844f-129">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="b844f-130">Domyślnie nowe działanie **pobrania** w projektancie będzie zawierać dwie gałęzie.</span><span class="sxs-lookup"><span data-stu-id="b844f-130">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="b844f-131">Aby dodać dodatkowe gałęzie, przeciągnij działanie **PickBranch** i upuść je obok istniejących gałęzi.</span><span class="sxs-lookup"><span data-stu-id="b844f-131">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="b844f-132">Działania można porzucić do działania **pobrania** w obszarze **wyzwalacza** lub w obszarze **akcji** dowolnego **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="b844f-132">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="b844f-133">Korzystanie z działania pobrania w kodzie</span><span class="sxs-lookup"><span data-stu-id="b844f-133">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="b844f-134"><xref:System.Activities.Statements.Pick>Działanie jest używane przez zapełnianie <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji <xref:System.Activities.Statements.PickBranch> działaniami.</span><span class="sxs-lookup"><span data-stu-id="b844f-134">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="b844f-135">Każdy z tych <xref:System.Activities.Statements.PickBranch> działań ma <xref:System.Activities.Statements.PickBranch.Trigger%2A> Właściwość typu <xref:System.Activities.Activity> .</span><span class="sxs-lookup"><span data-stu-id="b844f-135">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="b844f-136">Po zakończeniu określonego działania wykonywane jest wykonanie <xref:System.Activities.Statements.PickBranch.Action%2A> .</span><span class="sxs-lookup"><span data-stu-id="b844f-136">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="b844f-137">Poniższy przykład kodu ilustruje sposób użycia <xref:System.Activities.Statements.Pick> działania w celu zaimplementowania limitu czasu dla działania, które odczytuje wiersz z konsoli.</span><span class="sxs-lookup"><span data-stu-id="b844f-137">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
