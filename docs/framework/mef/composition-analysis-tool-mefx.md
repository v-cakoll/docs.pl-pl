---
title: Narzędzie do analizy kompozycji (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3777627caec7fc0d383804f71d9b7d3f09756fd
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894131"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="00172-102">Narzędzie do analizy kompozycji (Mefx)</span><span class="sxs-lookup"><span data-stu-id="00172-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="00172-103">Narzędzie do analizy kompozycji (Mefx) jest aplikacją wiersza polecenia, która analizuje pliki biblioteki (. dll) i aplikacji (exe) zawierające części Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="00172-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="00172-104">Głównym celem Mefx jest zapewnienie deweloperom metody diagnozowania błędów kompozycji w aplikacjach MEF, bez konieczności dodawania kodu śledzenia skomplikowany do samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00172-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="00172-105">Pomocne może być również zrozumienie części z biblioteki udostępnionej przez inną firmę.</span><span class="sxs-lookup"><span data-stu-id="00172-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="00172-106">W tym temacie opisano, jak używać Mefx i zawiera odwołanie do jego składni.</span><span class="sxs-lookup"><span data-stu-id="00172-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="00172-107">Pobieranie Mefx</span><span class="sxs-lookup"><span data-stu-id="00172-107">Getting Mefx</span></span>  
 <span data-ttu-id="00172-108">Mefx jest dostępny w witrynie GitHub w [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="00172-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="00172-109">Wystarczy pobrać i rozpakować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="00172-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="00172-110">Podstawowa składnia</span><span class="sxs-lookup"><span data-stu-id="00172-110">Basic Syntax</span></span>  
 <span data-ttu-id="00172-111">Mefx jest wywoływany z wiersza polecenia w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="00172-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="00172-112">Pierwszy zestaw argumentów określa pliki i katalogi, z których mają zostać załadowane części do analizy.</span><span class="sxs-lookup"><span data-stu-id="00172-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="00172-113">Określ plik z `/file:` przełącznikiem i katalog `/directory:` z przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="00172-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="00172-114">Można określić wiele plików lub katalogów, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="00172-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="00172-115">Każdy plik. dll lub. exe powinien być załadowany tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="00172-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="00172-116">Jeśli plik jest ładowany wielokrotnie, narzędzie może zwracać niepoprawne informacje.</span><span class="sxs-lookup"><span data-stu-id="00172-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="00172-117">Po wyświetleniu listy plików i katalogów należy określić polecenie i wszystkie opcje dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="00172-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="00172-118">Wyświetlanie listy dostępnych części</span><span class="sxs-lookup"><span data-stu-id="00172-118">Listing Available Parts</span></span>  
 <span data-ttu-id="00172-119">Użyj akcji `/parts` , aby wyświetlić listę wszystkich części zadeklarowanych w załadowanych plikach.</span><span class="sxs-lookup"><span data-stu-id="00172-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="00172-120">Wynik jest prostą listą nazw części.</span><span class="sxs-lookup"><span data-stu-id="00172-120">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="00172-121">Aby uzyskać więcej informacji na temat części, użyj `/verbose` opcji.</span><span class="sxs-lookup"><span data-stu-id="00172-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="00172-122">Spowoduje to wyjście z dodatkowych informacji dla wszystkich dostępnych części.</span><span class="sxs-lookup"><span data-stu-id="00172-122">This will output more information for all available parts.</span></span> <span data-ttu-id="00172-123">Aby uzyskać więcej informacji na temat pojedynczej części, użyj `/type` akcji `/parts`zamiast.</span><span class="sxs-lookup"><span data-stu-id="00172-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="00172-124">Wyświetlanie listy importów i eksportów</span><span class="sxs-lookup"><span data-stu-id="00172-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="00172-125">W `/imports` akcjach i `/exports` zostaną wystawione wszystkie zaimportowane części i wszystkie wyeksportowane części.</span><span class="sxs-lookup"><span data-stu-id="00172-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="00172-126">Można również wyświetlić listę składników, które zaimportują lub eksportują określony typ za `/importers` pomocą `/exporters` akcji lub.</span><span class="sxs-lookup"><span data-stu-id="00172-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="00172-127">Można również zastosować `/verbose` opcję do tych akcji.</span><span class="sxs-lookup"><span data-stu-id="00172-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="00172-128">Znajdowanie odrzuconych części</span><span class="sxs-lookup"><span data-stu-id="00172-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="00172-129">Po załadowaniu dostępnych części Mefx używa aparatu kompozycji MEF, aby je tworzyć.</span><span class="sxs-lookup"><span data-stu-id="00172-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="00172-130">Części, które nie mogą zostać pomyślnie złożone, są określane jako *odrzucone*.</span><span class="sxs-lookup"><span data-stu-id="00172-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="00172-131">Aby wyświetlić listę wszystkich odrzuconych części, `/rejected` Użyj akcji.</span><span class="sxs-lookup"><span data-stu-id="00172-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="00172-132">Można użyć `/verbose` opcji `/rejected` z akcją do drukowania szczegółowych informacji o odrzuconych częściach.</span><span class="sxs-lookup"><span data-stu-id="00172-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="00172-133">W poniższym przykładzie `ClassLibrary1` Biblioteka DLL `AddIn` zawiera `MemberPart` część, która importuje części i `ChainOne` .</span><span class="sxs-lookup"><span data-stu-id="00172-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="00172-134">`ChainOne`Importy `ChainTwo`, `ChainTwo` ale nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="00172-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="00172-135">Oznacza to, `ChainOne` że odrzucono, co spowoduje `AddIn` odrzucenie.</span><span class="sxs-lookup"><span data-stu-id="00172-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="00172-136">Poniżej przedstawiono pełne dane wyjściowe poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="00172-136">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="00172-137">Interesujące informacje są zawarte w `[Exception]` wynikach i. `[Unsuitable]`</span><span class="sxs-lookup"><span data-stu-id="00172-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="00172-138">`[Exception]` Wynik zawiera informacje o tym, dlaczego część została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="00172-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="00172-139">`[Unsuitable]` Wynik wskazuje, dlaczego nie można użyć części dopasowywania w inny sposób, aby wypełnić import; w tym przypadku, ponieważ ta część została odrzucona w przypadku brakujących importów.</span><span class="sxs-lookup"><span data-stu-id="00172-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="00172-140">Analizowanie przyczyn podstawowych</span><span class="sxs-lookup"><span data-stu-id="00172-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="00172-141">Jeśli kilka części jest połączonych w łańcuchu długich zależności, problem związany z częścią znajdującą się u dołu może spowodować odrzucenie całego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="00172-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="00172-142">Diagnozowanie tych problemów może być trudne, ponieważ główna przyczyna awarii nie zawsze jest oczywista.</span><span class="sxs-lookup"><span data-stu-id="00172-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="00172-143">Aby pomóc w rozwiązaniu problemu, możesz użyć `/causes` akcji, która próbuje znaleźć główną przyczynę odrzucenia kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="00172-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="00172-144">Użycie akcji z poprzedniego przykładu spowoduje wyświetlenie listy informacji dla `ChainOne`, których niewypełniony import jest główną przyczyną odrzucania `AddIn`. `/causes`</span><span class="sxs-lookup"><span data-stu-id="00172-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="00172-145">Akcja może być używana zarówno w normalnych, jak `/verbose` i w opcjach. `/causes`</span><span class="sxs-lookup"><span data-stu-id="00172-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00172-146">W większości przypadków Mefx będzie mógł zdiagnozować główną przyczynę niepowodzenia kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="00172-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="00172-147">Jednakże w przypadkach, gdy części są dodawane programowo do kontenera, przypadki obejmujące kontenery hierarchiczne lub przypadki z implementacją niestandardową `ExportProvider` , Mefx nie będzie w stanie zdiagnozować przyczyny.</span><span class="sxs-lookup"><span data-stu-id="00172-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="00172-148">Ogólnie opisane wcześniej w miarę możliwości należy unikać błędów, gdy błędy są zwykle trudne do zdiagnozowania.</span><span class="sxs-lookup"><span data-stu-id="00172-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="00172-149">Białe listy</span><span class="sxs-lookup"><span data-stu-id="00172-149">White Lists</span></span>  
 <span data-ttu-id="00172-150">`/whitelist` Opcja umożliwia określenie pliku tekstowego zawierającego listę części, które powinny być odrzucane.</span><span class="sxs-lookup"><span data-stu-id="00172-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="00172-151">Nieoczekiwane odrzucenia zostaną następnie oflagowane.</span><span class="sxs-lookup"><span data-stu-id="00172-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="00172-152">Może to być przydatne podczas analizowania niekompletnej biblioteki lub podbiblioteki, w której brakuje niektórych zależności.</span><span class="sxs-lookup"><span data-stu-id="00172-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="00172-153">Opcja może być stosowana `/rejected` do akcji lub `/causes`. `/whitelist`</span><span class="sxs-lookup"><span data-stu-id="00172-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="00172-154">Rozważmy plik o nazwie test. txt, który zawiera tekst "ClassLibrary1. ChainOne".</span><span class="sxs-lookup"><span data-stu-id="00172-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="00172-155">Jeśli uruchomisz `/rejected` akcję `/whitelist` z opcją w poprzednim przykładzie, spowoduje to wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="00172-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
