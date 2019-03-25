---
title: Wybieranie działania
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b9ee6c06377760d27bc54d39c1d1f3ecf67ea0d8
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409994"
---
# <a name="pick-activity"></a><span data-ttu-id="e02ce-102">Wybieranie działania</span><span class="sxs-lookup"><span data-stu-id="e02ce-102">Pick Activity</span></span>
<span data-ttu-id="e02ce-103"><xref:System.Activities.Statements.Pick> Działania upraszcza modelowania zestawu wyzwalaczy zdarzeń, następuje ich odpowiednie programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="e02ce-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="e02ce-104">A <xref:System.Activities.Statements.Pick> aktywności zawiera zbiór <xref:System.Activities.Statements.PickBranch> działań, gdzie każdy <xref:System.Activities.Statements.PickBranch> jest powiązany między <xref:System.Activities.Statements.PickBranch.Trigger%2A> działania i <xref:System.Activities.Statements.PickBranch.Action%2A> działania.</span><span class="sxs-lookup"><span data-stu-id="e02ce-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="e02ce-105">W czasie wykonywania wyzwalaczy dla wszystkich oddziałów są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="e02ce-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="e02ce-106">Po zakończeniu jeden wyzwalacz, następnie jest wykonywany swoje działania odpowiednie, a inne wyzwalacze są anulowane.</span><span class="sxs-lookup"><span data-stu-id="e02ce-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="e02ce-107">Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działanie jest podobne do [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="e02ce-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="e02ce-108">Poniższy zrzut ekranu z [przy użyciu działania wybierz](./samples/using-the-pick-activity.md) Przykładowy zestaw SDK zawiera działania Pick, za pomocą dwóch gałęzi.</span><span class="sxs-lookup"><span data-stu-id="e02ce-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="e02ce-109">Jedna gałąź ma wyzwalacza o nazwie **odczytu danych wejściowych**, niestandardowe działanie, które odczytuje dane wejściowe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e02ce-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="e02ce-110">Drugi gałęzi ma <xref:System.Activities.Statements.Delay> działania wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="e02ce-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="e02ce-111">Jeśli **odczytu danych wejściowych** działania odbiera dane przed <xref:System.Activities.Statements.Delay> zakończy działanie <xref:System.Activities.Statements.Delay> opóźnienie zostanie anulowane i powitanie zostanie zapisany do konsoli.</span><span class="sxs-lookup"><span data-stu-id="e02ce-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="e02ce-112">W przeciwnym razie, jeśli **odczytu danych wejściowych** działania nie odbiera danych w wyznaczonym czasie, a następnie zostanie anulowane i komunikat o limicie czasu będą zapisywane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="e02ce-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="e02ce-113">Jest to typowy wzorzec używany do zwiększenia limitu czasu żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="e02ce-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Wybieranie działania](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="e02ce-115">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e02ce-115">Best practices</span></span>  
 <span data-ttu-id="e02ce-116">Korzystając z pobrań, gałęzi, który jest wykonywany jest gałęzi, w której wyzwalacz zakończy się najpierw.</span><span class="sxs-lookup"><span data-stu-id="e02ce-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="e02ce-117">Koncepcyjnie wszystkie wyzwalacze są wykonywane równolegle, a jeden wyzwalacz może zostać wykonane większość swojej logiki zanim zostanie anulowane po zakończeniu kolejnego wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="e02ce-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="e02ce-118">Mając to na uwadze ogólne wytyczne, które należy wykonać podczas używanie działania Pick jest zaliczenie reprezentujący pojedyncze zdarzenie wyzwalacza i zostać umieszczona jako nieco logiki możliwie go.</span><span class="sxs-lookup"><span data-stu-id="e02ce-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="e02ce-119">W idealnym przypadku wyzwalacz powinien zawierać wystarczający logikę w celu odbierania zdarzeń, a przetwarzanie zdarzenia powinny należeć do akcji w gałęzi.</span><span class="sxs-lookup"><span data-stu-id="e02ce-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="e02ce-120">Ta metoda pozwala zmniejszyć nakładania się wykonywanie wyzwalacze.</span><span class="sxs-lookup"><span data-stu-id="e02ce-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="e02ce-121">Na przykład, rozważmy <xref:System.Activities.Statements.Pick> za pomocą dwóch wyzwalaczy, w którym każdy wyzwalacz ma <xref:System.ServiceModel.Activities.Receive> aktywności następuje dodatkowej logiki.</span><span class="sxs-lookup"><span data-stu-id="e02ce-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="e02ce-122">Jeśli dodatkowej logiki wprowadza punkt bezczynności, a następnie jest możliwość zarówno <xref:System.ServiceModel.Activities.Receive> działania pomyślne zakończenie działania.</span><span class="sxs-lookup"><span data-stu-id="e02ce-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="e02ce-123">Jeden wyzwalacz będzie w pełni zakończeniu podczas będzie innego częściowo ukończone.</span><span class="sxs-lookup"><span data-stu-id="e02ce-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="e02ce-124">W niektórych scenariuszach akceptowania wiadomości, a częściowo ukończenie przetwarzania go jest nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="e02ce-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="e02ce-125">W związku z tym korzystając z wbudowanych działań dotyczących komunikatów WF takich jak <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>, podczas gdy <xref:System.ServiceModel.Activities.Receive> jest powszechnie używana do wyzwalacza <xref:System.ServiceModel.Activities.SendReply> oraz innych logik należy umieścić w akcji, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e02ce-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="e02ce-126">Używanie działania Pick w Projektancie</span><span class="sxs-lookup"><span data-stu-id="e02ce-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="e02ce-127">Aby użyć wyboru w projektancie, Znajdź **wybierz** i **PickBranch** w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="e02ce-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="e02ce-128">Przeciąganie i upuszczanie **wybierz** na kanwę.</span><span class="sxs-lookup"><span data-stu-id="e02ce-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="e02ce-129">Domyślnie nowy **wybierz** działania w Projektancie będzie zawierać dwie gałęzie.</span><span class="sxs-lookup"><span data-stu-id="e02ce-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="e02ce-130">Aby dodać dodatkowe gałęzie, przeciągnij **PickBranch** działania i upuść je obok istniejącej gałęzi.</span><span class="sxs-lookup"><span data-stu-id="e02ce-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="e02ce-131">Działania mogą być upuszczone na **wybierz** działanie do albo **wyzwalacza** obszaru lub **akcji** obszar dowolnego **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="e02ce-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="e02ce-132">Używanie działania wybierz w kodzie</span><span class="sxs-lookup"><span data-stu-id="e02ce-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="e02ce-133"><xref:System.Activities.Statements.Pick> Działania jest używana przez wypełnianie jej <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji z <xref:System.Activities.Statements.PickBranch> działań.</span><span class="sxs-lookup"><span data-stu-id="e02ce-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="e02ce-134"><xref:System.Activities.Statements.PickBranch> Działania każdego mają <xref:System.Activities.Statements.PickBranch.Trigger%2A> właściwości typu <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="e02ce-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="e02ce-135">Podczas działania określonego kończy wykonywanie, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.</span><span class="sxs-lookup"><span data-stu-id="e02ce-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="e02ce-136">Poniższy przykład kodu demonstruje sposób używania <xref:System.Activities.Statements.Pick> działanie, aby zaimplementować limitu czasu dla działania, który odczytuje wiersz z konsoli.</span><span class="sxs-lookup"><span data-stu-id="e02ce-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
