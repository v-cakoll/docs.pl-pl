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
# <a name="composition-analysis-tool-mefx"></a>Narzędzie do analizy kompozycji (Mefx)
Narzędzie analizy składu (Mefx) to aplikacja wiersza polecenia, która analizuje pliki biblioteki (.dll) i aplikacji (.exe) zawierające części managed extensibility Framework (MEF). Głównym celem Mefx jest zapewnienie deweloperom sposób diagnozowania błędów składu w swoich aplikacjach MEF bez konieczności dodawania uciążliwego kodu śledzenia do samej aplikacji. Może być również przydatne, aby pomóc zrozumieć części z biblioteki dostarczonej przez stronę trzecią. W tym temacie opisano sposób używania mefx i zawiera odwołanie do jego składni.  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a>Pierwsze Mefx  
 Mefx jest dostępny na GitHub w [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Wystarczy pobrać i rozpakować narzędzie.  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a>Składnia podstawowa  
 Mefx jest wywoływany z wiersza polecenia w następującym formacie:  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 Pierwszy zestaw argumentów określa pliki i katalogi, z których mają być ładowane części do analizy. Określ plik `/file:` z przełącznikiem i katalog `/directory:` z przełącznikiem. Można określić wiele plików lub katalogów, jak pokazano w poniższym przykładzie:  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> Każdy plik dll lub .exe powinien być ładowany tylko jeden raz. Jeśli plik jest ładowany wiele razy, narzędzie może zwrócić nieprawidłowe informacje.  
  
 Po liście plików i katalogów należy określić polecenie i wszystkie opcje dla tego polecenia.  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a>Wystawianie dostępnych części  
 Użyj `/parts` akcji, aby wyświetlić listę wszystkich części zadeklarowanych w załadowanych plikach. Wynikiem jest prosta lista nazw części.  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Aby uzyskać więcej informacji na `/verbose` temat części, użyj opcji. Spowoduje to wysunie więcej informacji dla wszystkich dostępnych części. Aby uzyskać więcej informacji o pojedynczej części, użyj `/type` akcji zamiast `/parts`.  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a>Wykaz importu i eksportu  
 Akcje `/imports` `/exports` i będą wymieniać odpowiednio wszystkie importowane części i wszystkie wyeksportowane części. Można również wyświetlić listę części, które importują `/importers` `/exporters` lub eksportują określony typ za pomocą akcji lub.  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Można również zastosować `/verbose` tę opcję do tych akcji.  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a>Znajdowanie odrzuconych części  
 Po załadowaniu dostępnych części, Mefx używa silnika kompozycji MEF do ich komponowania. Części, których nie można pomyślnie skomponować, są określane jako *odrzucone*. Aby wyświetlić listę wszystkich `/rejected` odrzuconych części, użyj akcji.  
  
 Można użyć `/verbose` tej opcji `/rejected` z akcją, aby wydrukować szczegółowe informacje o odrzuconych częściach. W poniższym przykładzie `ClassLibrary1` biblioteka `AddIn` DLL zawiera `MemberPart` część, która importuje i `ChainOne` części. `ChainOne`importu `ChainTwo`, `ChainTwo` ale nie istnieje. Oznacza to, że `ChainOne` jest `AddIn` odrzucany, co powoduje, że należy go odrzucić.  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Poniżej przedstawiono pełne dane wyjściowe poprzedniego polecenia:  
  
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
  
 Interesujące informacje zawarte są `[Exception]` w `[Unsuitable]` i wyniki. Wynik `[Exception]` zawiera informacje o tym, dlaczego część została odrzucona. Wynik `[Unsuitable]` wskazuje, dlaczego nie można użyć części pasujące w przeciwnym razie do wypełnienia importu; w tym przypadku, ponieważ sama część ta została odrzucona z powodu braku przywozu.  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a>Analizowanie podstawowych przyczyn  
 Jeśli kilka części są połączone w długim łańcuchu zależności, problem z udziałem części w pobliżu dołu może spowodować cały łańcuch zostać odrzucone. Diagnozowanie tych problemów może być trudne, ponieważ główna przyczyna awarii nie zawsze jest oczywista. Aby pomóc w problemie, `/causes` możesz użyć akcji, która próbuje znaleźć główną przyczynę dowolnego kaskadowego odrzucenia.  
  
 Użycie `/causes` akcji w poprzednim przykładzie spowoduje `ChainOne`wyświetlenie tylko informacji dla , których `AddIn`niewypełniony import jest główną przyczyną odrzucenia programu . Akcja `/causes` może być używana zarówno `/verbose` w normalnych, jak i opcjach.  
  
> [!NOTE]
> W większości przypadków Mefx będzie w stanie zdiagnozować główną przyczynę awarii kaskadowej. Jednak w przypadkach, gdy części są dodawane programowo do kontenera, przypadki `ExportProvider` dotyczące kontenerów hierarchicznych lub przypadków dotyczących implementacji niestandardowych, Mefx nie będzie w stanie zdiagnozować przyczyny. Ogólnie rzecz biorąc, wcześniej opisanych przypadków należy unikać, jeśli to możliwe, jak błędy są na ogół trudne do zdiagnozowania.  
  
<a name="white_lists"></a>
## <a name="white-lists"></a>Białe listy  
 Ta `/whitelist` opcja umożliwia określenie pliku tekstowego zawierającego listę części, które mają zostać odrzucone. Nieoczekiwane odrzucenia zostaną oflagowane. Może to być przydatne podczas analizowania niekompletnej biblioteki lub poddo biblioteki, w której brakuje niektórych zależności. Opcja `/whitelist` może być stosowana `/rejected` do `/causes` akcji lub.  
  
 Należy wziąć pod uwagę plik o nazwie test.txt, który zawiera tekst "ClassLibrary1.ChainOne". Jeśli `/rejected` uruchomisz akcję `/whitelist` z opcją w poprzednim przykładzie, spowoduje to następujące dane wyjściowe:  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
