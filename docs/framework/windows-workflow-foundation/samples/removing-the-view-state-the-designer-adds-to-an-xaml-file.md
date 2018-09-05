---
title: Usuwanie stanu widoku Projektanta dodaje do pliku XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: ed2fda0bb66b2c8fe58c60acc6f80b9e9c8e984e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524955"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="775b5-102">Usuwanie stanu widoku Projektanta dodaje do pliku XAML</span><span class="sxs-lookup"><span data-stu-id="775b5-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="775b5-103">W tym przykładzie pokazano, jak utworzyć klasę, która jest pochodną <xref:System.Windows.Markup.XamlWriter> i usuwa wyświetlanie stanu z pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="775b5-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="775b5-104"> zapisuje informacje w dokumencie XAML, który jest znany jako stan widoku.</span><span class="sxs-lookup"><span data-stu-id="775b5-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="775b5-105">Wyświetl stan odnosi się do informacje, które są wymagane w czasie projektowania, takie jak układ pozycjonowanie, i które nie są wymagane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="775b5-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="775b5-106"> Wstawia tych informacji do dokumentu XAML jest edytowany.</span><span class="sxs-lookup"><span data-stu-id="775b5-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="775b5-107"> zapisuje stan widoku w pliku XAML z `mc:Ignorable` atrybutu, dzięki czemu te informacje nie został załadowany, gdy środowisko uruchomieniowe ładuje plik XAML.</span><span class="sxs-lookup"><span data-stu-id="775b5-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="775b5-108">W tym przykładzie pokazano, jak utworzyć klasę, która powoduje usunięcie tego widoku stanu podczas przetwarzania węzłów XAML.</span><span class="sxs-lookup"><span data-stu-id="775b5-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="775b5-109">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="775b5-109">Discussion</span></span>  
 <span data-ttu-id="775b5-110">W tym przykładzie pokazano, jak utworzyć niestandardowy Edytor.</span><span class="sxs-lookup"><span data-stu-id="775b5-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="775b5-111">Aby utworzyć niestandardowy Edytor XAML, należy utworzyć klasę, która dziedziczy po elemencie <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="775b5-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="775b5-112">Autorzy XAML często są zagnieżdżone, jest typowy do śledzenia "wewnętrzny" zapisywania XAML.</span><span class="sxs-lookup"><span data-stu-id="775b5-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="775b5-113">Te "wewnętrzny" autorzy można traktować jako odwołanie do pozostałych stosu moduły zapisujące XAML, dzięki czemu możesz mieć wiele punktów wejścia do pracy i następnie poprzez delegowanie przekazać przetwarzania do pozostałej części stosu.</span><span class="sxs-lookup"><span data-stu-id="775b5-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="775b5-114">W tym przykładzie istnieje kilka elementów zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="775b5-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="775b5-115">Jeden jest sprawdzenie, czy element zapisywana jest z projektanta przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="775b5-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="775b5-116">Należy pamiętać, że to również musiał użycie innych typów z przestrzeni nazw projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="775b5-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="775b5-117">Tworzy to również stosu XAML elementów członkowskich, które są używane podczas rekursywnego przesyłania strumień węzłów.</span><span class="sxs-lookup"><span data-stu-id="775b5-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="775b5-118">Praca pozostała tego przykładu stopniu znajduje się w <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.</span><span class="sxs-lookup"><span data-stu-id="775b5-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
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
  
 <span data-ttu-id="775b5-119">Kolejne metody, a następnie sprawdź, czy nadal znajdują się w kontenerze stanu widoku, a jeśli tak, wróć i nie przekazuj węzeł w dół stosu składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="775b5-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
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
  
 <span data-ttu-id="775b5-120">Aby użyć niestandardowego Edytor XAML, możesz musi zostać połączony je ze sobą w stosie autorzy XAML.</span><span class="sxs-lookup"><span data-stu-id="775b5-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="775b5-121">Poniższy kod pokazuje, jak może być używany.</span><span class="sxs-lookup"><span data-stu-id="775b5-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="775b5-122">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="775b5-122">To use this sample</span></span>  
  
1. <span data-ttu-id="775b5-123">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="775b5-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="775b5-124">Otwórz wiersz polecenia i przejdź do katalogu, w którym ViewStageCleaningWriter.exe jest wbudowana.</span><span class="sxs-lookup"><span data-stu-id="775b5-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="775b5-125">Uruchomienie pliku Workflow1.xaml ViewStateCleaningWriter.exe.</span><span class="sxs-lookup"><span data-stu-id="775b5-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="775b5-126">Składnia dla pliku wykonywalnego jest wyświetlana w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="775b5-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="775b5-127">Spowoduje to wygenerowanie pliku XAML do \[outfile], która zawiera wszystkie jej informacje o stanie widoku usunięte.</span><span class="sxs-lookup"><span data-stu-id="775b5-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="775b5-128">Aby uzyskać <xref:System.Activities.Statements.Sequence> przepływu pracy, liczba wirtualizacji wskazówki są usuwane.</span><span class="sxs-lookup"><span data-stu-id="775b5-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="775b5-129">Powoduje to projektanta Aby ponownie Oblicz układ następnym razem, gdy jest on ładowany.</span><span class="sxs-lookup"><span data-stu-id="775b5-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="775b5-130">Kiedy korzystać z tej próbki dla <xref:System.Activities.Statements.Flowchart>, pozycjonowanie i wiersza informacji o routingu są usuwane, a w kolejnych ładowanie do projektanta, wszystkie działania są ułożone w lewej części ekranu.</span><span class="sxs-lookup"><span data-stu-id="775b5-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="775b5-131">Aby utworzyć przykładowy plik XAML do użytku z tego przykładu</span><span class="sxs-lookup"><span data-stu-id="775b5-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="775b5-132">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b5-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="775b5-133">Utwórz nową aplikację konsoli przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="775b5-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="775b5-134">Przeciąganie i upuszczanie kilka działania na kanwę</span><span class="sxs-lookup"><span data-stu-id="775b5-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="775b5-135">Zapisz plik XAML przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="775b5-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="775b5-136">Sprawdź plik XAML, aby wyświetlić widok stanu dołączone właściwości.</span><span class="sxs-lookup"><span data-stu-id="775b5-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="775b5-137">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="775b5-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="775b5-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="775b5-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="775b5-139">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="775b5-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="775b5-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="775b5-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
