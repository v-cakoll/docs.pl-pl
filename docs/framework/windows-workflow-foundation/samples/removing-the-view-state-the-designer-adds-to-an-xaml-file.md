---
title: Dodaje usuwanie stanu widoku projektanta do pliku XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 66966668bb91a857503a82449633f8dd1ae621b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="118b3-102">Dodaje usuwanie stanu widoku projektanta do pliku XAML</span><span class="sxs-lookup"><span data-stu-id="118b3-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="118b3-103">Ten przykład przedstawia sposób tworzenia klasy pochodnej z <xref:System.Windows.Markup.XamlWriter> i usuwa wyświetlania stanu z pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="118b3-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="118b3-104">zapisuje informacje do dokumentu XAML, znany jako stan widoku.</span><span class="sxs-lookup"><span data-stu-id="118b3-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="118b3-105">Stan widoku odwołuje się do informacji, które jest wymagany w czasie projektowania, takie jak układ rozmieszczania, który nie jest wymagany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="118b3-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="118b3-106">Wstawia te informacje do dokumentu XAML jest edytowany.</span><span class="sxs-lookup"><span data-stu-id="118b3-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="118b3-107">zapisuje stan widoku w pliku XAML z `mc:Ignorable` atrybutu, dlatego te informacje nie został załadowany, gdy środowisko uruchomieniowe ładuje plik XAML.</span><span class="sxs-lookup"><span data-stu-id="118b3-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="118b3-108">W tym przykładzie pokazano, jak utworzyć klasę, która usuwa informacje o stanie tego widoku podczas przetwarzania węzłów XAML.</span><span class="sxs-lookup"><span data-stu-id="118b3-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="118b3-109">Omówienie</span><span class="sxs-lookup"><span data-stu-id="118b3-109">Discussion</span></span>  
 <span data-ttu-id="118b3-110">Ten przykład przedstawia sposób tworzenia niestandardowego modułu zapisującego.</span><span class="sxs-lookup"><span data-stu-id="118b3-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="118b3-111">Do tworzenia niestandardowych zapisywania XAML, Utwórz klasę, która dziedziczy <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="118b3-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="118b3-112">Jak często są zagnieżdżone autorów XAML, jest typowe do śledzenia "wewnętrzne" zapisywania XAML.</span><span class="sxs-lookup"><span data-stu-id="118b3-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="118b3-113">Te "wewnętrzne" zapisywania można traktować jako odwołanie do stosu pozostałych składników zapisywania XAML, co pozwala mieć wiele punktów wejścia do pracy i następnie poprzez delegowanie przekazać przetwarzanie reszta stosu.</span><span class="sxs-lookup"><span data-stu-id="118b3-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="118b3-114">W tym przykładzie istnieje kilka elementy.</span><span class="sxs-lookup"><span data-stu-id="118b3-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="118b3-115">Jeden jest sprawdzenie, czy element zapisywana jest z projektanta przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="118b3-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="118b3-116">Należy pamiętać, że to również usuwa użycie innych typów z projektanta przestrzeni nazw w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="118b3-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="118b3-117">Daje to stosu XAML elementów członkowskich, które są używane podczas przechodzenia przez strumień węzłów.</span><span class="sxs-lookup"><span data-stu-id="118b3-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="118b3-118">Praca pozostała tego przykładu przede wszystkim znajduje się w <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.</span><span class="sxs-lookup"><span data-stu-id="118b3-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
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
  
 <span data-ttu-id="118b3-119">Kolejne metody, a następnie sprawdź, czy nadal znajdują się w kontenerze stan widoku, a jeśli tak, wróć i nie są przekazywane węzeł w dół stosu składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="118b3-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
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
  
 <span data-ttu-id="118b3-120">Aby użyć niestandardowej zapisywania XAML, możesz musi łańcuch go w stosie składników zapisywania XAML.</span><span class="sxs-lookup"><span data-stu-id="118b3-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="118b3-121">Poniższy kod przedstawia sposób może być używany.</span><span class="sxs-lookup"><span data-stu-id="118b3-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="118b3-122">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="118b3-122">To use this sample</span></span>  
  
1. <span data-ttu-id="118b3-123">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="118b3-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="118b3-124">Otwórz wiersz polecenia i przejdź do katalogu, w którym ViewStageCleaningWriter.exe jest wbudowana.</span><span class="sxs-lookup"><span data-stu-id="118b3-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="118b3-125">Uruchom ViewStateCleaningWriter.exe Workflow1.xaml pliku.</span><span class="sxs-lookup"><span data-stu-id="118b3-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="118b3-126">W poniższym przykładzie przedstawiono składnię pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="118b3-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="118b3-127">To generuje plik XAML do \[outfile], która zawiera wszystkie jego Wyświetl informacje o stanie usunięte.</span><span class="sxs-lookup"><span data-stu-id="118b3-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="118b3-128">Aby uzyskać <xref:System.Activities.Statements.Sequence> przepływu pracy, liczba wirtualizacji wskazówki są usuwane.</span><span class="sxs-lookup"><span data-stu-id="118b3-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="118b3-129">Powoduje to projektanta, aby ponownie Oblicz układ następnym razem, gdy jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="118b3-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="118b3-130">Jeśli używasz tego przykładu dla <xref:System.Activities.Statements.Flowchart>, pozycjonowanie i linii routingu informacje zostaną usunięte i wszystkie działania w kolejnych ładowania do projektanta, stos po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="118b3-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="118b3-131">Aby utworzyć przykładowy plik XAML do użytku z tego przykładu</span><span class="sxs-lookup"><span data-stu-id="118b3-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="118b3-132">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="118b3-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="118b3-133">Utwórz nową aplikację konsoli przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="118b3-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="118b3-134">Przeciągnij i upuść kilka działań na kanwę</span><span class="sxs-lookup"><span data-stu-id="118b3-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="118b3-135">Zapisz plik XAML przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="118b3-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="118b3-136">Sprawdź plik XAML, aby wyświetlić widok stanu dołączone właściwości.</span><span class="sxs-lookup"><span data-stu-id="118b3-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="118b3-137">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="118b3-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="118b3-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="118b3-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="118b3-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="118b3-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="118b3-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="118b3-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
