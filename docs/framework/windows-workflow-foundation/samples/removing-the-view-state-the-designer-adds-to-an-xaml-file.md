---
title: Usuwanie stanu widoku, który Projektant dodaje do pliku XAML — WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715622"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="fbaaf-102">Usuwanie stanu widoku, który Projektant dodaje do pliku XAML</span><span class="sxs-lookup"><span data-stu-id="fbaaf-102">Removing the view state the designer adds to an XAML file</span></span>

<span data-ttu-id="fbaaf-103">Ten przykład pokazuje, jak utworzyć klasę, która dziedziczy po <xref:System.Xaml.XamlWriter> i usuwa stan widoku z pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-103">This sample demonstrates how to create a class that derives from <xref:System.Xaml.XamlWriter> and removes view state from a XAML file.</span></span> <span data-ttu-id="fbaaf-104">System Windows Projektant przepływu pracy zapisuje informacje w dokumencie XAML, który jest znany jako stan widoku.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-104">Windows Workflow Designer writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="fbaaf-105">Stan widoku odwołuje się do informacji wymaganych w czasie projektowania, takich jak pozycjonowanie układu, które nie są wymagane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> <span data-ttu-id="fbaaf-106">Projektant przepływu pracy wstawia te informacje do dokumentu XAML w trakcie jego edycji.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-106">Workflow Designer inserts this information into the XAML document as it is edited.</span></span> <span data-ttu-id="fbaaf-107">Projektant przepływu pracy zapisuje stan widoku w pliku XAML z atrybutem `mc:Ignorable`, więc te informacje nie zostaną załadowane, gdy środowisko uruchomieniowe załaduje plik XAML.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-107">Workflow Designer writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="fbaaf-108">Ten przykład pokazuje, jak utworzyć klasę, która usuwa informacje o stanie widoku podczas przetwarzania węzłów XAML.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="fbaaf-109">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="fbaaf-109">Discussion</span></span>

<span data-ttu-id="fbaaf-110">Ten przykład pokazuje, jak utworzyć niestandardowy moduł zapisujący.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-110">This sample demonstrates how to create a custom writer.</span></span>

<span data-ttu-id="fbaaf-111">Aby utworzyć niestandardowy składnik zapisywania XAML, Utwórz klasę, która dziedziczy po <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-111">To build a custom XAML writer, create a class that inherits from <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="fbaaf-112">Ponieważ moduły zapisujące XAML często są zagnieżdżone, typowe jest śledzenie "wewnętrznego" składnika zapisywania XAML.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="fbaaf-113">Te "wewnętrzne" składowe można traktować jako odwołanie do pozostałego stosu autorów XAML, co pozwala na wykonywanie wielu punktów wejścia do pracy, a następnie delegowanie przetwarzania do pozostałej części stosu.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

<span data-ttu-id="fbaaf-114">W tym przykładzie istnieje kilka interesujących rzeczy.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="fbaaf-115">Jednym z nich jest sprawdzenie, czy element jest zapisywany, pochodzi z przestrzeni nazw projektanta.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="fbaaf-116">Należy zauważyć, że spowoduje to również przydzielenie użycia innych typów z przestrzeni nazw projektanta w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

<span data-ttu-id="fbaaf-117">Powoduje to również utworzenie stosu elementów członkowskich XAML, które są używane podczas przechodzenia przez strumień węzła.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="fbaaf-118">Pozostała część pracy tego przykładu jest w dużym stopniu zawarta w metodzie `WriteStartMember`.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-118">The remaining work of this sample is largely contained in the `WriteStartMember` method.</span></span>

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

<span data-ttu-id="fbaaf-119">Kolejne metody, a następnie sprawdzają, czy nadal znajdują się w kontenerze Stanów widoku, a jeśli tak, zwracają i nie przekazują węzła w dół stosu składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

<span data-ttu-id="fbaaf-120">Aby użyć niestandardowego składnika zapisywania XAML, należy łańcuchować go razem w stosie modułów zapisujących XAML.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="fbaaf-121">Poniższy kod przedstawia, jak można go użyć.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a><span data-ttu-id="fbaaf-122">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fbaaf-122">To use this sample</span></span>

1. <span data-ttu-id="fbaaf-123">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania ViewStateCleaningWriter. sln.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="fbaaf-124">Otwórz wiersz polecenia i przejdź do katalogu, w którym utworzono plik ViewStageCleaningWriter. exe.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="fbaaf-125">Uruchom ViewStateCleaningWriter. exe w pliku Workflow1. XAML.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="fbaaf-126">Składnia dla pliku wykonywalnego jest pokazana w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="fbaaf-127">Spowoduje to wyjście z pliku XAML w celu \[pliku], który ma wszystkie usunięte informacje o stanie widoku.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="fbaaf-128">W przypadku przepływu pracy <xref:System.Activities.Statements.Sequence> są usuwane różne wskazówki dotyczące wirtualizacji.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="fbaaf-129">Powoduje to, że projektant będzie ponownie obliczał układ przy następnym załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="fbaaf-130">Gdy użyjesz tego przykładu dla <xref:System.Activities.Statements.Flowchart>, wszystkie informacje o rozłożeniu i trasie są usuwane i po następnym załadowaniu do projektanta wszystkie działania są układane po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="fbaaf-131">Aby utworzyć przykładowy plik XAML do użycia z tym przykładem</span><span class="sxs-lookup"><span data-stu-id="fbaaf-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="fbaaf-132">Otwórz program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="fbaaf-133">Utwórz nową aplikację konsoli przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="fbaaf-134">Przeciągnij i upuść kilka działań na kanwę</span><span class="sxs-lookup"><span data-stu-id="fbaaf-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="fbaaf-135">Zapisz plik XAML przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="fbaaf-136">Sprawdź plik XAML, aby wyświetlić właściwości widoku dołączonego stanu.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbaaf-137">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fbaaf-138">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="fbaaf-138">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fbaaf-139">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbaaf-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fbaaf-140">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fbaaf-140">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
