---
title: Wybieranie działania
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 672de5fd3df5e8dde6c54118503bf2a11353b116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182892"
---
# <a name="pick-activity"></a><span data-ttu-id="172d5-102">Wybieranie działania</span><span class="sxs-lookup"><span data-stu-id="172d5-102">Pick Activity</span></span>
<span data-ttu-id="172d5-103">Działanie <xref:System.Activities.Statements.Pick> upraszcza modelowanie zestawu wyzwalaczy zdarzeń, po których następuje ich odpowiednie programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="172d5-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="172d5-104">Działanie <xref:System.Activities.Statements.Pick> zawiera zbiór <xref:System.Activities.Statements.PickBranch> działań, gdzie <xref:System.Activities.Statements.PickBranch> każdy jest parowanie między działaniem <xref:System.Activities.Statements.PickBranch.Trigger%2A> a działaniem. <xref:System.Activities.Statements.PickBranch.Action%2A></span><span class="sxs-lookup"><span data-stu-id="172d5-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="172d5-105">W czasie wykonywania wyzwalacze dla wszystkich gałęzi są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="172d5-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="172d5-106">Po zakończeniu jednego wyzwalacza, a następnie jego odpowiednie działanie jest wykonywane, a wszystkie inne wyzwalacze są anulowane.</span><span class="sxs-lookup"><span data-stu-id="172d5-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="172d5-107">Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działania jest podobny do działania .NET Framework <xref:System.Workflow.Activities.ListenActivity> 3.5.</span><span class="sxs-lookup"><span data-stu-id="172d5-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="172d5-108">Poniższy zrzut ekranu z przy użyciu przy [użyciu przystawek SDK działania](./samples/using-the-pick-activity.md) pokazuje Działanie pobrania z dwóch gałęzi.</span><span class="sxs-lookup"><span data-stu-id="172d5-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="172d5-109">Jedna gałąź ma wyzwalacz o nazwie **Odczyt danych wejściowych**, działanie niestandardowe, które odczytuje dane wejściowe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="172d5-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="172d5-110">Druga gałąź <xref:System.Activities.Statements.Delay> ma wyzwalacz działania.</span><span class="sxs-lookup"><span data-stu-id="172d5-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="172d5-111">Jeśli działanie **do odczytu danych wejściowych** odbiera dane przed <xref:System.Activities.Statements.Delay> zakończeniem działania, <xref:System.Activities.Statements.Delay> Opóźnienie zostanie anulowane, a powitanie zostanie zapisane na konsoli.</span><span class="sxs-lookup"><span data-stu-id="172d5-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="172d5-112">W przeciwnym razie jeśli działanie **do odczytu danych wejściowych** nie odbierze danych w wyznaczonym czasie, zostanie ono anulowane, a na konsoli zostanie zapisany komunikat limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="172d5-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="172d5-113">Jest to typowy wzorzec używany do dodawania limitu czasu do dowolnej akcji.</span><span class="sxs-lookup"><span data-stu-id="172d5-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Wybieranie działania](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="172d5-115">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="172d5-115">Best practices</span></span>  
 <span data-ttu-id="172d5-116">Podczas korzystania z Pick, gałąź, która wykonuje jest gałąź, której wyzwalacz kończy się jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="172d5-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="172d5-117">Koncepcyjnie wszystkie wyzwalacze są wykonywane równolegle, a jeden wyzwalacz mógł wykonać większość jego logiki, zanim zostanie anulowany przez ukończenie innego wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="172d5-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="172d5-118">Mając to na uwadze, ogólne wytyczne do naśladowania podczas korzystania z Pick działania jest traktowanie wyzwalacza jako reprezentujący pojedyncze zdarzenie i umieścić jak najmniej logiki, jak to możliwe do niego.</span><span class="sxs-lookup"><span data-stu-id="172d5-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="172d5-119">W idealnym przypadku wyzwalacz powinien zawierać wystarczającą ilość logiki, aby otrzymać zdarzenie, a całe przetwarzanie tego zdarzenia powinno przejść do akcji gałęzi.</span><span class="sxs-lookup"><span data-stu-id="172d5-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="172d5-120">Ta metoda minimalizuje ilość nakładania się między wykonywanie wyzwalaczy.</span><span class="sxs-lookup"><span data-stu-id="172d5-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="172d5-121">Na przykład należy <xref:System.Activities.Statements.Pick> wziąć pod uwagę z dwóch <xref:System.ServiceModel.Activities.Receive> wyzwalaczy, gdzie każdy wyzwalacz zawiera działanie, a następnie dodatkowe logiki.</span><span class="sxs-lookup"><span data-stu-id="172d5-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="172d5-122">Jeśli dodatkowa logika wprowadza punkt bezczynności, istnieje możliwość, <xref:System.ServiceModel.Activities.Receive> że oba działania zostaną pomyślnie ukończone.</span><span class="sxs-lookup"><span data-stu-id="172d5-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="172d5-123">Jeden wyzwalacz zostanie w pełni ukończony, podczas gdy drugi zostanie częściowo ukończony.</span><span class="sxs-lookup"><span data-stu-id="172d5-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="172d5-124">W niektórych scenariuszach akceptowanie wiadomości, a następnie częściowe jej przetwarzanie jest niedopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="172d5-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="172d5-125">W związku z tym podczas korzystania z wbudowanej <xref:System.ServiceModel.Activities.SendReply>obsługi <xref:System.ServiceModel.Activities.Receive> wiadomości WF, takich <xref:System.ServiceModel.Activities.SendReply> jak <xref:System.ServiceModel.Activities.Receive> i , podczas gdy jest powszechnie używany w wyzwalaczu i inne logiki powinny być wprowadzane w akcji, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="172d5-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="172d5-126">Korzystanie z działania Pobranie w projektancie</span><span class="sxs-lookup"><span data-stu-id="172d5-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="172d5-127">Aby użyć opcji Wybierz w projektancie, znajdź **przycisk Wybierz** i **Wybierz** w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="172d5-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="172d5-128">Przeciągnij i upuść **Wybierz** na kanwę.</span><span class="sxs-lookup"><span data-stu-id="172d5-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="172d5-129">Domyślnie nowe działanie **pobrania** w projektancie będzie zawierać dwie gałęzie.</span><span class="sxs-lookup"><span data-stu-id="172d5-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="172d5-130">Aby dodać dodatkowe gałęzie, przeciągnij działanie **PickBranch** i upuść je obok istniejących gałęzi.</span><span class="sxs-lookup"><span data-stu-id="172d5-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="172d5-131">Działania można upuścić na **działanie pobrania** w obszarze **Wyzwalacz** lub w obszarze **Akcja** dowolnego **pickbrancha**.</span><span class="sxs-lookup"><span data-stu-id="172d5-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="172d5-132">Korzystanie z działania pobrania w kodzie</span><span class="sxs-lookup"><span data-stu-id="172d5-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="172d5-133">Działanie <xref:System.Activities.Statements.Pick> jest używane przez wypełnianie <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.PickBranch> jego kolekcji działaniami.</span><span class="sxs-lookup"><span data-stu-id="172d5-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="172d5-134">Działania <xref:System.Activities.Statements.PickBranch> mają <xref:System.Activities.Statements.PickBranch.Trigger%2A> właściwość typu <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="172d5-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="172d5-135">Po zakończeniu wykonywania określonego działania, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.</span><span class="sxs-lookup"><span data-stu-id="172d5-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="172d5-136">Poniższy przykład kodu pokazuje, <xref:System.Activities.Statements.Pick> jak używać działania do implementacji limitu czasu dla działania, które odczytuje wiersz z konsoli.</span><span class="sxs-lookup"><span data-stu-id="172d5-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
