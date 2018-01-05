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
ms.workload: dotnet
ms.openlocfilehash: d6e5ab22ff2fe382fa2a266e3180cb34f970cc48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="composition-analysis-tool-mefx"></a>Narzędzie do analizy kompozycji (Mefx)
Narzędzie do analizy kompozycji (Mefx) jest aplikacją wiersza polecenia, która analizuje biblioteki (.dll) i pliki aplikacji (.exe) zawierający części Managed Extensibility Framework (MEF). Głównym celem Mefx ma umożliwiają deweloperom diagnozowanie błędów kompozycji w swoich aplikacjach MEF bez konieczności Dodaj kod śledzenia skomplikowane do samej aplikacji. Może być również przydatne do zrozumienia składniki Report Part z biblioteki udostępnione przez innych firm. W tym temacie opisano sposób użycia Mefx i znajdują się informacje na jego składni.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Pobieranie Mefx  
 Mefx jest dostępna w witrynie GitHub pod [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Po prostu Pobierz i Rozpakuj narzędzie.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Podstawowa składnia  
 Mefx jest wywoływana z poziomu wiersza polecenia w następującym formacie:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 Pierwszy zestaw argumentów Określ pliki i katalogi, z którego można załadować części dla analizy. Określ plik z `/file:` przełącznika i katalog o `/directory:` przełącznika. Można określić wiele plików lub katalogów, jak pokazano w poniższym przykładzie:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Każdy .dll lub .exe powinien można ładować tylko jeden raz. Jeśli plik został załadowany wiele razy, narzędzie może zwracać niepoprawne informacje.  
  
 Po listę plików i katalogów należy określić polecenia i opcje dla tego polecenia.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Wyświetlanie listy dostępnych części  
 Użyj `/parts` akcji, aby wyświetlić listę wszystkich części zadeklarowany w plikach załadowane. Wynik jest to prosta lista nazw części.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Aby uzyskać więcej informacji na temat części, użyj `/verbose` opcji. Dane wyjściowe dodatkowe informacje dotyczące wszystkich dostępnych części. Aby uzyskać więcej informacji na temat jednej części, należy użyć `/type` akcji zamiast `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>Wyświetlanie listy importu i eksportu  
 `/imports` i `/exports` akcje będzie zawierała listę wszystkich importowanych części i wszystkie części wyeksportowanego odpowiednio. Można również podać części, których importowania lub eksportowania określonego typu za pomocą `/importers` lub `/exporters` akcje.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Można także zastosować `/verbose` opcję, aby te akcje.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Znajdowanie odrzucone części  
 Po załadowaniu dostępne części, Mefx używa aparatu kompozycji MEF ich utworzenie. Elementy, które nie mogą być składane pomyślnie są określane jako *odrzucone*. Aby wyświetlić listę wszystkich odrzucone części, użyj `/rejected` akcji.  
  
 Można użyć `/verbose` opcję z `/rejected` akcji, aby wydrukować szczegółowe informacje o odrzucone części. W poniższym przykładzie `ClassLibrary1` biblioteki DLL zawiera `AddIn` części, który importuje `MemberPart` i `ChainOne` części. `ChainOne`Importuje `ChainTwo`, ale `ChainTwo` nie istnieje. Oznacza to, że `ChainOne` zostaje odrzucona, co powoduje, że `AddIn` odrzucona.  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Poniżej przedstawiono pełne dane wyjściowe poprzedniego polecenia:  
  
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
  
 Interesujące informacje znajdują się w `[Exception]` i `[Unsuitable]` wyników. `[Exception]` Wynik zawiera informacje o Dlaczego części został odrzucony. `[Unsuitable]` Wyników wskazuje na to, dlaczego części dopasowywania w przeciwnym razie nie można użyć do wypełnienia importu; w takim przypadku powodu części sam odrzucone importów Brak.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Analizowanie podstawowy powoduje, że  
 Kilka fragmentów są połączone w łańcuchu zależności długie, problem obejmujące w dolnej części może spowodować całego łańcucha odrzucona. Diagnozowanie problemów może być trudne, ponieważ głównej przyczyny błędu nie jest zawsze widoczne. Aby ułatwić ten problem, można użyć `/causes` akcji, który próbuje odnaleźć przyczynę żadnych kaskadowych odrzucenia.  
  
 Przy użyciu `/causes` działania w poprzednim przykładzie pojawi się lista tylko informacje o `ChainOne`, którego niewypełniony importu jest główną przyczynę odrzucenia `AddIn`. `/causes` Akcji mogą być używane w obu normalny i `/verbose` opcje.  
  
> [!NOTE]
>  W większości przypadków Mefx będzie można zdiagnozować główną przyczynę awarii w kaskadowego. Jednak w przypadki, w której części są dodawane programowo do kontenera, przypadkach dotyczących hierarchiczna kontenery lub przypadków obejmujących niestandardowe `ExportProvider` implementacji, Mefx nie będzie można zdiagnozować przyczynę. Ogólnie rzecz biorąc opisany wcześniej przypadków należy unikać Jeśli to możliwe, ponieważ błędy są zazwyczaj trudne do diagnozowania.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Białe listy  
 `/whitelist` Opcji można określić plik tekstowy, który zawiera elementy, które powinny być odrzucane. Nieoczekiwany odrzuceń zostaną następnie oflagowane. Może to być przydatne podczas analizowania biblioteki niekompletne lub podrzędne biblioteki, która nie ma niektórych zależności. `/whitelist` Opcję można zastosować do `/rejected` lub `/causes` akcje.  
  
 Należy wziąć pod uwagę plik o nazwie test.txt, który zawiera tekst "ClassLibrary1.ChainOne". Po uruchomieniu `/rejected` akcji o `/whitelist` opcji w poprzednim przykładzie powoduje wygenerowanie następujących danych wyjściowych:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
