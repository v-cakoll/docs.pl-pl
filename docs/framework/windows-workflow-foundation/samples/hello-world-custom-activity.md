---
title: Niestandardowe działanie Hello World
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470778"
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="4b93f-102">Niestandardowe działanie Hello World</span><span class="sxs-lookup"><span data-stu-id="4b93f-102">Hello World Custom Activity</span></span>
<span data-ttu-id="4b93f-103">Niniejszy przykład pokazuje kilka kluczowych funkcji programu Windows Workflow Foundation (WF), w tym jak utworzyć proste działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4b93f-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="4b93f-104">Niektóre funkcje przedstawione w tym przykładzie tworzenia działań niestandardowych w języku C# i za pomocą `in` i `out` argumentów (<xref:System.Activities.InArgument> i <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="4b93f-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4b93f-105">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4b93f-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4b93f-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4b93f-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4b93f-107">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4b93f-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b93f-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4b93f-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="4b93f-109">Tworzenie przepływu pracy w kodzie</span><span class="sxs-lookup"><span data-stu-id="4b93f-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="4b93f-110">W tym przykładzie są tworzone dwa działania niestandardowe, przy użyciu kodu C#.</span><span class="sxs-lookup"><span data-stu-id="4b93f-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="4b93f-111">Zarówno działań niestandardowych dziedziczyć bezpośrednio lub pośrednio <xref:System.Activities.Activity%601> zwracać pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="4b93f-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="4b93f-112">Zaletą używania ogólnego zwracanej wartości, a nie dziedziczy z inną niż ogólna <xref:System.Activities.Activity> klasy, jest to, że niektóre działania (takie jak <xref:System.Activities.Statements.Assign>) mogą uzyskać dostępu wartość zwracana, gdy jest używana jako część złożone działania.</span><span class="sxs-lookup"><span data-stu-id="4b93f-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="4b93f-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="4b93f-113">AppendString</span></span>  
 <span data-ttu-id="4b93f-114">To działanie dziedziczy <xref:System.Activities.Activity%601>i wykorzystuje <xref:System.Activities.Statements.Assign> działanie, które łączy ze sobą dwa ciągi.</span><span class="sxs-lookup"><span data-stu-id="4b93f-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="4b93f-115">Dołącz ciąg</span><span class="sxs-lookup"><span data-stu-id="4b93f-115">Prepend String</span></span>  
 <span data-ttu-id="4b93f-116">To działanie dziedziczy bezpośrednio z <xref:System.Activities.CodeActivity%601>i tworzy funkcje podobne do `AppendString` działania, które używa logiki zaimplementowane w kod, a nie jest złożony z istniejących działań.</span><span class="sxs-lookup"><span data-stu-id="4b93f-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="4b93f-117">Następujące pliki znajdują się w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b93f-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="4b93f-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="4b93f-118">AppendString.cs</span></span>  
 <span data-ttu-id="4b93f-119">Niestandardowe działanie, które dołącza ciągi ze sobą.</span><span class="sxs-lookup"><span data-stu-id="4b93f-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="4b93f-120">On przyjmuje ciąg i łączy ją z ciągiem literału tekstowego "— mówi hello world" do formularza komunikat o ukończeniu jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="4b93f-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="4b93f-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="4b93f-121">PrependString.cs</span></span>  
 <span data-ttu-id="4b93f-122">To działanie prefiksy wstępnie zdefiniowane parametry do ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="4b93f-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="4b93f-123">Sequence1.XAML</span><span class="sxs-lookup"><span data-stu-id="4b93f-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="4b93f-124">Przepływ pracy, który używa `AppendString` i `PrependString` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4b93f-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="4b93f-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="4b93f-125">Program.cs</span></span>  
 <span data-ttu-id="4b93f-126">Program, który uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="4b93f-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4b93f-127">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4b93f-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="4b93f-128">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="4b93f-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4b93f-129">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4b93f-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4b93f-130">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="4b93f-130">To run the solution, press F5.</span></span>