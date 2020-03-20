---
title: Narzędzie do analizy kompozycji (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: 7d0acf16ace5aad60b32b7139a58a258fb080ee0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181298"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="5f21b-102">Narzędzie do analizy kompozycji (Mefx)</span><span class="sxs-lookup"><span data-stu-id="5f21b-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="5f21b-103">Narzędzie analizy składu (Mefx) to aplikacja wiersza polecenia, która analizuje pliki biblioteki (.dll) i aplikacji (.exe) zawierające części managed extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="5f21b-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="5f21b-104">Głównym celem Mefx jest zapewnienie deweloperom sposób diagnozowania błędów składu w swoich aplikacjach MEF bez konieczności dodawania uciążliwego kodu śledzenia do samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f21b-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="5f21b-105">Może być również przydatne, aby pomóc zrozumieć części z biblioteki dostarczonej przez stronę trzecią.</span><span class="sxs-lookup"><span data-stu-id="5f21b-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="5f21b-106">W tym temacie opisano sposób używania mefx i zawiera odwołanie do jego składni.</span><span class="sxs-lookup"><span data-stu-id="5f21b-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a><span data-ttu-id="5f21b-107">Pierwsze Mefx</span><span class="sxs-lookup"><span data-stu-id="5f21b-107">Getting Mefx</span></span>  
 <span data-ttu-id="5f21b-108">Mefx jest dostępny na GitHub w [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="5f21b-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="5f21b-109">Wystarczy pobrać i rozpakować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="5f21b-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a><span data-ttu-id="5f21b-110">Składnia podstawowa</span><span class="sxs-lookup"><span data-stu-id="5f21b-110">Basic Syntax</span></span>  
 <span data-ttu-id="5f21b-111">Mefx jest wywoływany z wiersza polecenia w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="5f21b-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="5f21b-112">Pierwszy zestaw argumentów określa pliki i katalogi, z których mają być ładowane części do analizy.</span><span class="sxs-lookup"><span data-stu-id="5f21b-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="5f21b-113">Określ plik `/file:` z przełącznikiem i katalog `/directory:` z przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="5f21b-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="5f21b-114">Można określić wiele plików lub katalogów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5f21b-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="5f21b-115">Każdy plik dll lub .exe powinien być ładowany tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="5f21b-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="5f21b-116">Jeśli plik jest ładowany wiele razy, narzędzie może zwrócić nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="5f21b-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="5f21b-117">Po liście plików i katalogów należy określić polecenie i wszystkie opcje dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f21b-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a><span data-ttu-id="5f21b-118">Wystawianie dostępnych części</span><span class="sxs-lookup"><span data-stu-id="5f21b-118">Listing Available Parts</span></span>  
 <span data-ttu-id="5f21b-119">Użyj `/parts` akcji, aby wyświetlić listę wszystkich części zadeklarowanych w załadowanych plikach.</span><span class="sxs-lookup"><span data-stu-id="5f21b-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="5f21b-120">Wynikiem jest prosta lista nazw części.</span><span class="sxs-lookup"><span data-stu-id="5f21b-120">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="5f21b-121">Aby uzyskać więcej informacji na `/verbose` temat części, użyj opcji.</span><span class="sxs-lookup"><span data-stu-id="5f21b-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="5f21b-122">Spowoduje to wysunie więcej informacji dla wszystkich dostępnych części.</span><span class="sxs-lookup"><span data-stu-id="5f21b-122">This will output more information for all available parts.</span></span> <span data-ttu-id="5f21b-123">Aby uzyskać więcej informacji o pojedynczej części, użyj `/type` akcji zamiast `/parts`.</span><span class="sxs-lookup"><span data-stu-id="5f21b-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a><span data-ttu-id="5f21b-124">Wykaz importu i eksportu</span><span class="sxs-lookup"><span data-stu-id="5f21b-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="5f21b-125">Akcje `/imports` `/exports` i będą wymieniać odpowiednio wszystkie importowane części i wszystkie wyeksportowane części.</span><span class="sxs-lookup"><span data-stu-id="5f21b-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="5f21b-126">Można również wyświetlić listę części, które importują `/importers` `/exporters` lub eksportują określony typ za pomocą akcji lub.</span><span class="sxs-lookup"><span data-stu-id="5f21b-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="5f21b-127">Można również zastosować `/verbose` tę opcję do tych akcji.</span><span class="sxs-lookup"><span data-stu-id="5f21b-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a><span data-ttu-id="5f21b-128">Znajdowanie odrzuconych części</span><span class="sxs-lookup"><span data-stu-id="5f21b-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="5f21b-129">Po załadowaniu dostępnych części, Mefx używa silnika kompozycji MEF do ich komponowania.</span><span class="sxs-lookup"><span data-stu-id="5f21b-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="5f21b-130">Części, których nie można pomyślnie skomponować, są określane jako *odrzucone*.</span><span class="sxs-lookup"><span data-stu-id="5f21b-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="5f21b-131">Aby wyświetlić listę wszystkich `/rejected` odrzuconych części, użyj akcji.</span><span class="sxs-lookup"><span data-stu-id="5f21b-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="5f21b-132">Można użyć `/verbose` tej opcji `/rejected` z akcją, aby wydrukować szczegółowe informacje o odrzuconych częściach.</span><span class="sxs-lookup"><span data-stu-id="5f21b-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="5f21b-133">W poniższym przykładzie `ClassLibrary1` biblioteka `AddIn` DLL zawiera `MemberPart` część, która importuje i `ChainOne` części.</span><span class="sxs-lookup"><span data-stu-id="5f21b-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="5f21b-134">`ChainOne`importu `ChainTwo`, `ChainTwo` ale nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5f21b-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="5f21b-135">Oznacza to, że `ChainOne` jest `AddIn` odrzucany, co powoduje, że należy go odrzucić.</span><span class="sxs-lookup"><span data-stu-id="5f21b-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="5f21b-136">Poniżej przedstawiono pełne dane wyjściowe poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5f21b-136">The following shows the complete output of the previous command:</span></span>  
  
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
  
 <span data-ttu-id="5f21b-137">Interesujące informacje zawarte są `[Exception]` w `[Unsuitable]` i wyniki.</span><span class="sxs-lookup"><span data-stu-id="5f21b-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="5f21b-138">Wynik `[Exception]` zawiera informacje o tym, dlaczego część została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="5f21b-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="5f21b-139">Wynik `[Unsuitable]` wskazuje, dlaczego nie można użyć części pasujące w przeciwnym razie do wypełnienia importu; w tym przypadku, ponieważ sama część ta została odrzucona z powodu braku przywozu.</span><span class="sxs-lookup"><span data-stu-id="5f21b-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a><span data-ttu-id="5f21b-140">Analizowanie podstawowych przyczyn</span><span class="sxs-lookup"><span data-stu-id="5f21b-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="5f21b-141">Jeśli kilka części są połączone w długim łańcuchu zależności, problem z udziałem części w pobliżu dołu może spowodować cały łańcuch zostać odrzucone.</span><span class="sxs-lookup"><span data-stu-id="5f21b-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="5f21b-142">Diagnozowanie tych problemów może być trudne, ponieważ główna przyczyna awarii nie zawsze jest oczywista.</span><span class="sxs-lookup"><span data-stu-id="5f21b-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="5f21b-143">Aby pomóc w problemie, `/causes` możesz użyć akcji, która próbuje znaleźć główną przyczynę dowolnego kaskadowego odrzucenia.</span><span class="sxs-lookup"><span data-stu-id="5f21b-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="5f21b-144">Użycie `/causes` akcji w poprzednim przykładzie spowoduje `ChainOne`wyświetlenie tylko informacji dla , których `AddIn`niewypełniony import jest główną przyczyną odrzucenia programu .</span><span class="sxs-lookup"><span data-stu-id="5f21b-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="5f21b-145">Akcja `/causes` może być używana zarówno `/verbose` w normalnych, jak i opcjach.</span><span class="sxs-lookup"><span data-stu-id="5f21b-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f21b-146">W większości przypadków Mefx będzie w stanie zdiagnozować główną przyczynę awarii kaskadowej.</span><span class="sxs-lookup"><span data-stu-id="5f21b-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="5f21b-147">Jednak w przypadkach, gdy części są dodawane programowo do kontenera, przypadki `ExportProvider` dotyczące kontenerów hierarchicznych lub przypadków dotyczących implementacji niestandardowych, Mefx nie będzie w stanie zdiagnozować przyczyny.</span><span class="sxs-lookup"><span data-stu-id="5f21b-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="5f21b-148">Ogólnie rzecz biorąc, wcześniej opisanych przypadków należy unikać, jeśli to możliwe, jak błędy są na ogół trudne do zdiagnozowania.</span><span class="sxs-lookup"><span data-stu-id="5f21b-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>
## <a name="white-lists"></a><span data-ttu-id="5f21b-149">Białe listy</span><span class="sxs-lookup"><span data-stu-id="5f21b-149">White Lists</span></span>  
 <span data-ttu-id="5f21b-150">Ta `/whitelist` opcja umożliwia określenie pliku tekstowego zawierającego listę części, które mają zostać odrzucone.</span><span class="sxs-lookup"><span data-stu-id="5f21b-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="5f21b-151">Nieoczekiwane odrzucenia zostaną oflagowane.</span><span class="sxs-lookup"><span data-stu-id="5f21b-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="5f21b-152">Może to być przydatne podczas analizowania niekompletnej biblioteki lub poddo biblioteki, w której brakuje niektórych zależności.</span><span class="sxs-lookup"><span data-stu-id="5f21b-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="5f21b-153">Opcja `/whitelist` może być stosowana `/rejected` do `/causes` akcji lub.</span><span class="sxs-lookup"><span data-stu-id="5f21b-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="5f21b-154">Należy wziąć pod uwagę plik o nazwie test.txt, który zawiera tekst "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="5f21b-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="5f21b-155">Jeśli `/rejected` uruchomisz akcję `/whitelist` z opcją w poprzednim przykładzie, spowoduje to następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5f21b-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
