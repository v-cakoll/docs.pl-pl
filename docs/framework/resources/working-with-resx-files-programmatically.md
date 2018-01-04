---
title: Praca programistyczna z plikami .resx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17c2cee97c3347a98a015e8526e436815378eed0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-resx-files-programmatically"></a>Praca programistyczna z plikami .resx
Ponieważ pliki zasobów (resx) XML musi składać się z dobrze zdefiniowany XML, dołączeniu nagłówka, który należy wykonać określonego schematu następuje dane w pary nazwa/wartość, może się okazać, że ręczne tworzenie tych plików jest podatne na błędy. Alternatywnie pliki .resx można utworzyć programowo, używając typy i składniki w bibliotece klas programu .NET Framework. Biblioteka klas programu .NET Framework umożliwia również pobrać zasobów, które są przechowywane w plikach resx. W tym temacie wyjaśniono, jak można użyć typów i członków <xref:System.Resources> przestrzeni nazw, aby pracować z plikami .resx.  
  
 Należy pamiętać, że w tym artykule omówiono pracy z danymi XML (resx) plików, które zawierają zasoby obiektów. Aby uzyskać informacje na temat pracy z plików binarnych zasobów, które zostały osadzone w zestawach, zobacz <xref:System.Resources.ResourceManager> tematu.  
  
> [!WARNING]
>  Brak metody pracy z plikami .resx innych niż programowo. Po dodaniu pliku zasobu do projektu programu Visual Studio Visual Studio udostępnia interfejs do tworzenia i obsługi pliku .resx, a następnie automatycznie konwertuje pliku .resx w pliku .resources w czasie kompilacji. Edytor tekstu służy również do manipulowania pliku .resx bezpośrednio. Jednak aby uniknąć uszkodzenia plików, należy zachować ostrożność nie zmodyfikować informacje binarne, który jest przechowywany w pliku.  
  
## <a name="creating-a-resx-file"></a>Tworzenie pliku .resx  
 Można użyć <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> klasy w celu utworzenia pliku .resx programowo, wykonując następujące czynności:  
  
1.  Utwórz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu przez wywołanie metody <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> — metoda i podając nazwę pliku .resx. Nazwa pliku musi zawierać rozszerzenia resx. Jeśli można utworzyć wystąpienia <xref:System.Resources.ResXResourceWriter> obiektu w `using` blok, nie masz jawnie wywołać <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody w kroku 3.  
  
2.  Wywołanie <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody dla każdego zasobu, które chcesz dodać do pliku. Użyj przeciążeń tej metody, aby dodać ciąg, obiekt i danych binarnych (tablicę bajtów). Jeśli zasób jest obiektem, muszą podlegać serializacji.  
  
3.  Wywołanie <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody, aby wygenerować plik zasobów i zwolnić wszystkie zasoby. Jeśli <xref:System.Resources.ResXResourceWriter> obiekt został utworzony w ramach `using` bloku zasobów są zapisywane w pliku .resx i zasoby używane przez <xref:System.Resources.ResXResourceWriter> obiektu są wydawane na końcu `using` bloku.  
  
 Wynikowy plik .resx ma odpowiedni nagłówek i `data` tagu dla każdego zasobu dodane przez <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.  
  
> [!WARNING]
>  Pliki zasobów nie należy używać do przechowywania haseł, informacji poufnych lub dane prywatne.  
  
 Poniższy przykład tworzy plik .resx o nazwie CarResources.resx, która przechowuje sześć ciągów, ikony i dwa obiekty zdefiniowane przez aplikację (dwie `Automobile` obiektów). Należy pamiętać, że `Automobile` klasy, która jest zdefiniowana i w tym przykładzie, jest oznaczane <xref:System.SerializableAttribute> atrybutu.  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  Visual Studio umożliwia również utworzenie pliki resx. W czasie kompilacji Visual Studio będzie korzystać [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) Aby przekonwertować pliku .resx zasobu binarnego (.resources) plików, a także osadzony w zestawie aplikacji lub zestawu satelickiego.  
  
 Nie można osadzić pliku .resx w środowisku uruchomieniowym pliku wykonywalnego lub skompiluj go do zestawu satelickiego. Należy przekonwertować pliku .resx w plik zasobu binarnego (.resources) przy użyciu [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Wynikowy plik .resources następnie mogą być osadzone w zestawie aplikacji lub zestawu satelickiego. Aby uzyskać więcej informacji, zobacz [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
## <a name="enumerating-resources"></a>Wyliczanie zasobów  
 W niektórych przypadkach można pobrać wszystkich zasobów, a nie konkretnego zasobu z pliku resx. Aby to zrobić, można użyć <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> klasy, która udostępnia moduł wyliczający dla wszystkich zasobów w pliku resx. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Klasa implementuje <xref:System.Collections.IDictionaryEnumerator>, która zwraca <xref:System.Collections.DictionaryEntry> obiekt, który reprezentuje określonego zasobu dla każdej iteracji pętli. Jego <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> właściwość zwraca klucz zasobu i jego <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> zwraca wartość zasobu.  
  
 Poniższy przykład tworzy <xref:System.Resources.ResXResourceReader> obiektu pliku CarResources.resx utworzonego w poprzednim przykładzie i iteruje pliku zasobu. Dodaje dwa `Automobile` obiektów, które są zdefiniowane w pliku zasobu do <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiektu który dodaje pięć sześć ciągów <xref:System.Collections.SortedList> obiektu. Wartości w <xref:System.Collections.SortedList> obiektu są konwertowane na tablicy parametrów, która jest używana do wyświetlania nagłówki kolumn do konsoli. `Automobile` Wartości właściwości są również wyświetlane w konsoli.  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## <a name="retrieving-a-specific-resource"></a>Trwa pobieranie określonego zasobu  
 Oprócz wyliczania elementów w pliku .resx, można pobrać określonego zasobu o nazwie za pomocą <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> klasy. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Metoda pobiera wartości zasobu ciągu o nazwie. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Metoda pobiera wartość nazwanego obiektu lub dane binarne. Metoda zwraca obiekt, który następnie musi być rzutowanie (C#) lub przekonwertować (w języku Visual Basic) do odpowiedniego typu obiektu.  
  
 Poniższy przykład pobiera ciąg podpisu formularza i ikona nazwy zasobu. Również pobranie przez aplikację `Automobile` obiekty używane w poprzednim przykładzie i wyświetla je w <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## <a name="converting-resx-files-to-binary-resources-files"></a>Konwertowanie plików binarnych .resources pliki .resx  
 Konwertowanie plików .resx na pliki zasobów binarnych osadzonego (.resources) oferuje istotne korzyści. Pliki .resx łatwych do odczytu i obsługa podczas tworzenia aplikacji, są one dołączone rzadko Zakończono aplikacji. Jeśli są one dystrybuowane za pomocą aplikacji, istnieje jako osobne pliki oprócz plik wykonywalny aplikacji i jej towarzyszące bibliotek. Z kolei .resources — pliki są osadzone w pliku wykonywalnym aplikacji lub jej zestawy towarzyszące. Ponadto dla aplikacji zlokalizowanych polegania na pliki .resx w czasie wykonywania miejscach odpowiedzialność za obsługę zasobów rezerwowej na dewelopera. Z kolei został utworzony zestaw zestawy satelickie, zawierające pliki osadzonych .resources, środowisko uruchomieniowe języka wspólnego obsługuje proces rezerwowy zasobów.  
  
 Aby przekonwertować pliku .resx w plik .resources, należy użyć [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), który ma następującą składnię podstawowe:  
  
 **ResGen.exe** *.resxFilename*  
  
 Wynik jest plik zasobu binarnego, który ma taką samą nazwę pliku głównego pliku .resx i rozszerzenie pliku .resources. Ten plik można skompilować następnie do pliku wykonywalnego lub biblioteki, w czasie kompilacji. Jeśli używasz kompilator Visual Basic, aby osadzić pliku zasobów w plik wykonywalny aplikacji należy użyć następującej składni:  
  
 **vbc —** *filename* **/.vb Resource:** *.resourcesFilename*  
  
 Jeśli używasz języka C#, ma następującą składnię:  
  
 **CSC** *filename* **/.cs Resource:** *.resourcesFilename*  
  
 Plik .resources można również osadzać w zestawie satelickim przy użyciu [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), który ma następującą składnię podstawowe:  
  
 **Al** *resourcesFilename* **/out:** *assemblyFilename*  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Resgen.exe (generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)
