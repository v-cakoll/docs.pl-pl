---
title: "Narzędzie do analizy kompozycji (Mefx)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 740ba87fd247e05b1bc32e3732819514ba2806ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="0454e-102">Narzędzie do analizy kompozycji (Mefx)</span><span class="sxs-lookup"><span data-stu-id="0454e-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="0454e-103">Narzędzie do analizy kompozycji (Mefx) jest aplikacją wiersza polecenia, która analizuje biblioteki (.dll) i pliki aplikacji (.exe) zawierający części Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="0454e-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="0454e-104">Głównym celem Mefx ma umożliwiają deweloperom diagnozowanie błędów kompozycji w swoich aplikacjach MEF bez konieczności Dodaj kod śledzenia skomplikowane do samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0454e-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="0454e-105">Może być również przydatne do zrozumienia składniki Report Part z biblioteki udostępnione przez innych firm.</span><span class="sxs-lookup"><span data-stu-id="0454e-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="0454e-106">W tym temacie opisano sposób użycia Mefx i znajdują się informacje na jego składni.</span><span class="sxs-lookup"><span data-stu-id="0454e-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="0454e-107">Pobieranie Mefx</span><span class="sxs-lookup"><span data-stu-id="0454e-107">Getting Mefx</span></span>  
 <span data-ttu-id="0454e-108">Mefx jest dostępna w witrynie GitHub pod [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="0454e-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="0454e-109">Po prostu Pobierz i Rozpakuj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="0454e-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="0454e-110">Podstawowa składnia</span><span class="sxs-lookup"><span data-stu-id="0454e-110">Basic Syntax</span></span>  
 <span data-ttu-id="0454e-111">Mefx jest wywoływana z poziomu wiersza polecenia w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="0454e-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="0454e-112">Pierwszy zestaw argumentów Określ pliki i katalogi, z którego można załadować części dla analizy.</span><span class="sxs-lookup"><span data-stu-id="0454e-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="0454e-113">Określ plik z `/file:` przełącznika i katalog o `/directory:` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="0454e-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="0454e-114">Można określić wiele plików lub katalogów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0454e-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="0454e-115">Każdy .dll lub .exe powinien można ładować tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="0454e-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="0454e-116">Jeśli plik został załadowany wiele razy, narzędzie może zwracać niepoprawne informacje.</span><span class="sxs-lookup"><span data-stu-id="0454e-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="0454e-117">Po listę plików i katalogów należy określić polecenia i opcje dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0454e-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="0454e-118">Wyświetlanie listy dostępnych części</span><span class="sxs-lookup"><span data-stu-id="0454e-118">Listing Available Parts</span></span>  
 <span data-ttu-id="0454e-119">Użyj `/parts` akcji, aby wyświetlić listę wszystkich części zadeklarowany w plikach załadowane.</span><span class="sxs-lookup"><span data-stu-id="0454e-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="0454e-120">Wynik jest to prosta lista nazw części.</span><span class="sxs-lookup"><span data-stu-id="0454e-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="0454e-121">Aby uzyskać więcej informacji na temat części, użyj `/verbose` opcji.</span><span class="sxs-lookup"><span data-stu-id="0454e-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="0454e-122">Dane wyjściowe dodatkowe informacje dotyczące wszystkich dostępnych części.</span><span class="sxs-lookup"><span data-stu-id="0454e-122">This will output more information for all available parts.</span></span> <span data-ttu-id="0454e-123">Aby uzyskać więcej informacji na temat jednej części, należy użyć `/type` akcji zamiast `/parts`.</span><span class="sxs-lookup"><span data-stu-id="0454e-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="0454e-124">Wyświetlanie listy importu i eksportu</span><span class="sxs-lookup"><span data-stu-id="0454e-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="0454e-125">`/imports` i `/exports` akcje będzie zawierała listę wszystkich importowanych części i wszystkie części wyeksportowanego odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0454e-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="0454e-126">Można również podać części, których importowania lub eksportowania określonego typu za pomocą `/importers` lub `/exporters` akcje.</span><span class="sxs-lookup"><span data-stu-id="0454e-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="0454e-127">Można także zastosować `/verbose` opcję, aby te akcje.</span><span class="sxs-lookup"><span data-stu-id="0454e-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="0454e-128">Znajdowanie odrzucone części</span><span class="sxs-lookup"><span data-stu-id="0454e-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="0454e-129">Po załadowaniu dostępne części, Mefx używa aparatu kompozycji MEF ich utworzenie.</span><span class="sxs-lookup"><span data-stu-id="0454e-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="0454e-130">Elementy, które nie mogą być składane pomyślnie są określane jako *odrzucone*.</span><span class="sxs-lookup"><span data-stu-id="0454e-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="0454e-131">Aby wyświetlić listę wszystkich odrzucone części, użyj `/rejected` akcji.</span><span class="sxs-lookup"><span data-stu-id="0454e-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="0454e-132">Można użyć `/verbose` opcję z `/rejected` akcji, aby wydrukować szczegółowe informacje o odrzucone części.</span><span class="sxs-lookup"><span data-stu-id="0454e-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="0454e-133">W poniższym przykładzie `ClassLibrary1` biblioteki DLL zawiera `AddIn` części, który importuje `MemberPart` i `ChainOne` części.</span><span class="sxs-lookup"><span data-stu-id="0454e-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="0454e-134">`ChainOne`Importuje `ChainTwo`, ale `ChainTwo` nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="0454e-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="0454e-135">Oznacza to, że `ChainOne` zostaje odrzucona, co powoduje, że `AddIn` odrzucona.</span><span class="sxs-lookup"><span data-stu-id="0454e-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="0454e-136">Poniżej przedstawiono pełne dane wyjściowe poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="0454e-136">The following shows the complete output of the previous command:</span></span>  
  
```  
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
  
 <span data-ttu-id="0454e-137">Interesujące informacje znajdują się w `[Exception]` i `[Unsuitable]` wyników.</span><span class="sxs-lookup"><span data-stu-id="0454e-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="0454e-138">`[Exception]` Wynik zawiera informacje o Dlaczego części został odrzucony.</span><span class="sxs-lookup"><span data-stu-id="0454e-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="0454e-139">`[Unsuitable]` Wyników wskazuje na to, dlaczego części dopasowywania w przeciwnym razie nie można użyć do wypełnienia importu; w takim przypadku powodu części sam odrzucone importów Brak.</span><span class="sxs-lookup"><span data-stu-id="0454e-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="0454e-140">Analizowanie podstawowy powoduje, że</span><span class="sxs-lookup"><span data-stu-id="0454e-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="0454e-141">Kilka fragmentów są połączone w łańcuchu zależności długie, problem obejmujące w dolnej części może spowodować całego łańcucha odrzucona.</span><span class="sxs-lookup"><span data-stu-id="0454e-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="0454e-142">Diagnozowanie problemów może być trudne, ponieważ głównej przyczyny błędu nie jest zawsze widoczne.</span><span class="sxs-lookup"><span data-stu-id="0454e-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="0454e-143">Aby ułatwić ten problem, można użyć `/causes` akcji, który próbuje odnaleźć przyczynę żadnych kaskadowych odrzucenia.</span><span class="sxs-lookup"><span data-stu-id="0454e-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="0454e-144">Przy użyciu `/causes` działania w poprzednim przykładzie pojawi się lista tylko informacje o `ChainOne`, którego niewypełniony importu jest główną przyczynę odrzucenia `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="0454e-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="0454e-145">`/causes` Akcji mogą być używane w obu normalny i `/verbose` opcje.</span><span class="sxs-lookup"><span data-stu-id="0454e-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0454e-146">W większości przypadków Mefx będzie można zdiagnozować główną przyczynę awarii w kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="0454e-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="0454e-147">Jednak w przypadki, w której części są dodawane programowo do kontenera, przypadkach dotyczących hierarchiczna kontenery lub przypadków obejmujących niestandardowe `ExportProvider` implementacji, Mefx nie będzie można zdiagnozować przyczynę.</span><span class="sxs-lookup"><span data-stu-id="0454e-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="0454e-148">Ogólnie rzecz biorąc opisany wcześniej przypadków należy unikać Jeśli to możliwe, ponieważ błędy są zazwyczaj trudne do diagnozowania.</span><span class="sxs-lookup"><span data-stu-id="0454e-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="0454e-149">Białe listy</span><span class="sxs-lookup"><span data-stu-id="0454e-149">White Lists</span></span>  
 <span data-ttu-id="0454e-150">`/whitelist` Opcji można określić plik tekstowy, który zawiera elementy, które powinny być odrzucane.</span><span class="sxs-lookup"><span data-stu-id="0454e-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="0454e-151">Nieoczekiwany odrzuceń zostaną następnie oflagowane.</span><span class="sxs-lookup"><span data-stu-id="0454e-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="0454e-152">Może to być przydatne podczas analizowania biblioteki niekompletne lub podrzędne biblioteki, która nie ma niektórych zależności.</span><span class="sxs-lookup"><span data-stu-id="0454e-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="0454e-153">`/whitelist` Opcję można zastosować do `/rejected` lub `/causes` akcje.</span><span class="sxs-lookup"><span data-stu-id="0454e-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="0454e-154">Należy wziąć pod uwagę plik o nazwie test.txt, który zawiera tekst "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="0454e-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="0454e-155">Po uruchomieniu `/rejected` akcji o `/whitelist` opcji w poprzednim przykładzie powoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="0454e-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
