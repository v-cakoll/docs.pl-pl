---
title: Dodaje usuwanie stanu widoku projektanta do pliku XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f63723c29c76854602308ba3e8d7e6dd65d9fb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="4ae92-102">Dodaje usuwanie stanu widoku projektanta do pliku XAML</span><span class="sxs-lookup"><span data-stu-id="4ae92-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="4ae92-103">Ten przykład przedstawia sposób tworzenia klasy pochodnej z <xref:System.Windows.Markup.XamlWriter> i usuwa wyświetlania stanu z pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="4ae92-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="4ae92-104"> zapisuje informacje do dokumentu XAML, znany jako stan widoku.</span><span class="sxs-lookup"><span data-stu-id="4ae92-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="4ae92-105">Stan widoku odwołuje się do informacji, które jest wymagany w czasie projektowania, takie jak układ rozmieszczania, który nie jest wymagany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4ae92-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="4ae92-106"> Wstawia te informacje do dokumentu XAML jest edytowany.</span><span class="sxs-lookup"><span data-stu-id="4ae92-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="4ae92-107"> zapisuje stan widoku w pliku XAML z `mc:Ignorable` atrybutu, dlatego te informacje nie został załadowany, gdy środowisko uruchomieniowe ładuje plik XAML.</span><span class="sxs-lookup"><span data-stu-id="4ae92-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="4ae92-108">W tym przykładzie pokazano, jak utworzyć klasę, która usuwa informacje o stanie tego widoku podczas przetwarzania węzłów XAML.</span><span class="sxs-lookup"><span data-stu-id="4ae92-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4ae92-109">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4ae92-109">Discussion</span></span>  
 <span data-ttu-id="4ae92-110">Ten przykład przedstawia sposób tworzenia niestandardowego modułu zapisującego.</span><span class="sxs-lookup"><span data-stu-id="4ae92-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="4ae92-111">Do tworzenia niestandardowych zapisywania XAML, Utwórz klasę, która dziedziczy <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4ae92-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="4ae92-112">Jak często są zagnieżdżone autorów XAML, jest typowe do śledzenia "wewnętrzne" zapisywania XAML.</span><span class="sxs-lookup"><span data-stu-id="4ae92-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="4ae92-113">Te "wewnętrzne" zapisywania można traktować jako odwołanie do stosu pozostałych składników zapisywania XAML, co pozwala mieć wiele punktów wejścia do pracy i następnie poprzez delegowanie przekazać przetwarzanie reszta stosu.</span><span class="sxs-lookup"><span data-stu-id="4ae92-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="4ae92-114">W tym przykładzie istnieje kilka elementy.</span><span class="sxs-lookup"><span data-stu-id="4ae92-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="4ae92-115">Jeden jest sprawdzenie, czy element zapisywana jest z projektanta przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4ae92-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="4ae92-116">Należy pamiętać, że to również usuwa użycie innych typów z projektanta przestrzeni nazw w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="4ae92-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="4ae92-117">Daje to stosu XAML elementów członkowskich, które są używane podczas przechodzenia przez strumień węzłów.</span><span class="sxs-lookup"><span data-stu-id="4ae92-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="4ae92-118">Praca pozostała tego przykładu przede wszystkim znajduje się w <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.</span><span class="sxs-lookup"><span data-stu-id="4ae92-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
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
  
 <span data-ttu-id="4ae92-119">Kolejne metody, a następnie sprawdź, czy nadal znajdują się w kontenerze stan widoku, a jeśli tak, wróć i nie są przekazywane węzeł w dół stosu składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="4ae92-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
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
  
 <span data-ttu-id="4ae92-120">Aby użyć niestandardowej zapisywania XAML, możesz musi łańcuch go w stosie składników zapisywania XAML.</span><span class="sxs-lookup"><span data-stu-id="4ae92-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="4ae92-121">Poniższy kod przedstawia sposób może być używany.</span><span class="sxs-lookup"><span data-stu-id="4ae92-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4ae92-122">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4ae92-122">To use this sample</span></span>  
  
1. <span data-ttu-id="4ae92-123">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="4ae92-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="4ae92-124">Otwórz wiersz polecenia i przejdź do katalogu, w którym ViewStageCleaningWriter.exe jest wbudowana.</span><span class="sxs-lookup"><span data-stu-id="4ae92-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="4ae92-125">Uruchom ViewStateCleaningWriter.exe Workflow1.xaml pliku.</span><span class="sxs-lookup"><span data-stu-id="4ae92-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="4ae92-126">W poniższym przykładzie przedstawiono składnię pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="4ae92-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="4ae92-127">To generuje plik XAML do \[outfile], która zawiera wszystkie jego Wyświetl informacje o stanie usunięte.</span><span class="sxs-lookup"><span data-stu-id="4ae92-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ae92-128">Aby uzyskać <xref:System.Activities.Statements.Sequence> przepływu pracy, liczba wirtualizacji wskazówki są usuwane.</span><span class="sxs-lookup"><span data-stu-id="4ae92-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="4ae92-129">Powoduje to projektanta, aby ponownie Oblicz układ następnym razem, gdy jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="4ae92-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="4ae92-130">Jeśli używasz tego przykładu dla <xref:System.Activities.Statements.Flowchart>, pozycjonowanie i linii routingu informacje zostaną usunięte i wszystkie działania w kolejnych ładowania do projektanta, stos po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="4ae92-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="4ae92-131">Aby utworzyć przykładowy plik XAML do użytku z tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4ae92-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="4ae92-132">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ae92-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="4ae92-133">Utwórz nową aplikację konsoli przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4ae92-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="4ae92-134">Przeciągnij i upuść kilka działań na kanwę</span><span class="sxs-lookup"><span data-stu-id="4ae92-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="4ae92-135">Zapisz plik XAML przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4ae92-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="4ae92-136">Sprawdź plik XAML, aby wyświetlić widok stanu dołączone właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ae92-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4ae92-137">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4ae92-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4ae92-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4ae92-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4ae92-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4ae92-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ae92-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4ae92-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
