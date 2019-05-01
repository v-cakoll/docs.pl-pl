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
ms.openlocfilehash: 6851ac334d439f2e5c0f6056f5226e3faa1503d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872342"
---
# <a name="composition-analysis-tool-mefx"></a>Narzędzie do analizy kompozycji (Mefx)
Narzędzie do analizy kompozycji (Mefx) jest aplikacją wiersza polecenia, który analizuje biblioteki (.dll) i pliki aplikacji (.exe), zawierający części Managed Extensibility Framework (MEF). Głównym celem Mefx jest umożliwiają deweloperom diagnozowanie błędów składu w swoich aplikacjach MEF nie wymaga, aby dodać kod śledzenia kłopotliwe do samej aplikacji. Również może być przydatne do zrozumienia składniki Report Part z biblioteki, dostarczone przez stronę trzecią. W tym temacie opisano sposób użycia Mefx i znajdują się informacje na jego składni.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Wprowadzenie Mefx  
 Mefx jest dostępna w witrynie GitHub pod [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Po prostu Pobierz i Rozpakuj narzędzie.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Podstawowa składnia  
 Mefx jest wywoływane z poziomu wiersza polecenia w następującym formacie:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 Pierwszy zestaw argumentów określić pliki i katalogi, z którego można załadować części do analizy. Określ plik z `/file:` przełącznika i katalog o `/directory:` przełącznika. Można określić wiele plików lub katalogów, jak pokazano w poniższym przykładzie:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Każdy plik .dll lub .exe powinien można ładować tylko jeden raz. Jeśli plik jest ładowany kilka razy, narzędzie może zwracać nieprawidłowe informacje.  
  
 Po listę plików i katalogów należy określić polecenia i opcje dla tego polecenia.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Wyświetlanie listy dostępnych części  
 Użyj `/parts` akcji, aby wyświetlić listę wszystkich części zadeklarowane w plikach załadowane. Wynik jest prostą listę nazw.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Aby uzyskać więcej informacji na temat poszczególnych użyj `/verbose` opcji. Dane wyjściowe dodatkowe informacje dotyczące wszystkich dostępnych części. Aby uzyskać więcej informacji na temat pojedynczą częścią, użyj `/type` akcji zamiast `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>Wyświetlanie listy importu i eksportu  
 `/imports` i `/exports` akcji spowoduje wyświetlenie listy wszystkich importowanych części i wszystkie części wyeksportowanego odpowiednio. Można również podać części, które importowania lub eksportowania danego typu przy użyciu `/importers` lub `/exporters` akcji.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Można również zastosować `/verbose` opcję, aby te akcje.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Znajdowanie odrzucone części  
 Po załadowaniu dostępnych części Mefx używa aparat kompozycji MEF do ich tworzenia. Części, które nie mogą być pomyślnie składane są określane jako *odrzucone*. Aby wyświetlić listę wszystkich części odrzucone, należy użyć `/rejected` akcji.  
  
 Możesz użyć `/verbose` z opcją `/rejected` akcji, aby wydrukować szczegółowe informacje o odrzucone części. W poniższym przykładzie `ClassLibrary1` Biblioteka DLL zawiera sekcję `AddIn` części, które importuje `MemberPart` i `ChainOne` części. `ChainOne` Importuje `ChainTwo`, ale `ChainTwo` nie istnieje. Oznacza to, że `ChainOne` została odrzucona, co powoduje, że `AddIn` odrzucona.  
  
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
  
 Interesujące informacje znajdują się w `[Exception]` i `[Unsuitable]` wyników. `[Exception]` Wynik zawiera informacje dotyczące przyczyny część została odrzucona. `[Unsuitable]` Wynik wskazuje, dlaczego część dopasowywania w przeciwnym razie nie można użyć do wypełnienia import, w tym przypadku powodu tę część samego odrzucone Brak importów.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Analizowanie podstawowy powoduje, że  
 Kilka elementów są połączone w łańcuchu zależności długie, problem z udziałem w dolnej części może spowodować cały łańcuch odrzucona. Diagnozowanie takich problemów może być trudne, ponieważ nie główną przyczynę niepowodzenia zawsze jest oczywiste. Aby pomóc w rozwiązaniu problemu, możesz użyć `/causes` akcji, która próbuje odnaleźć głównej przyczyny wszelkich kaskadowych odrzucenia.  
  
 Za pomocą `/causes` akcji w poprzednim przykładzie zwróciłaby listę tylko informacje o `ChainOne`, którego niewypełnionym import jest główną przyczynę odrzucenia `AddIn`. `/causes` Akcji mogą być używane w obu normalnego i `/verbose` opcje.  
  
> [!NOTE]
>  W większości przypadków Mefx będzie mógł zdiagnozować jej główną przyczynę błędów kaskadowych. Jednak w przypadki, gdzie części są dodane programowo do kontenera, przypadków obejmujących hierarchiczne kontenerów lub przypadków obejmujących niestandardowe `ExportProvider` implementacji Mefx nie będzie przyczynę. Ogólnie rzecz biorąc opisany wcześniej przypadków należy unikać w przypadku, gdy jest to możliwe, błędy są zazwyczaj trudny do zdiagnozowania.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Białe listy  
 `/whitelist` Opcji można określić plik tekstowy, który zawiera listę elementów, które powinny zostać odrzucone. Nieoczekiwany odrzuceń zostaną następnie oflagowane. Może to być przydatne podczas analizowania niekompletne biblioteki lub bibliotekę podrzędną, która nie ma niektórych zależności. `/whitelist` Opcji mogą być stosowane do `/rejected` lub `/causes` akcji.  
  
 Należy wziąć pod uwagę w pliku o nazwie jako, które zawiera tekst "ClassLibrary1.ChainOne". Po uruchomieniu `/rejected` akcji z `/whitelist` opcję poprzedni przykład generuje następujące wyniki:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
