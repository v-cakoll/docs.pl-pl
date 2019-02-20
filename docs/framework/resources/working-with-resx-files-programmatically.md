---
title: Praca programistyczna z plikami .resx
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cddb7985c8763e5c18ecca0255f4f3556e03719e
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441453"
---
# <a name="working-with-resx-files-programmatically"></a>Praca programistyczna z plikami .resx
Ponieważ pliki zasobów (.resx) XML musi zawierać dobrze zdefiniowanych XML, w tym nagłówek, który musi być zgodny ze schematem określonego następuje dane w pary nazwa/wartość może się okazać, że ręcznego tworzenia tych plików jest podatne na błędy. Jako alternatywę pliki resx można utworzyć programowo, przy użyciu typów i elementów członkowskich w bibliotece klas programu .NET. Biblioteki klas platformy .NET umożliwia również pobrać zasoby, które są przechowywane w plikach resx. W tym temacie wyjaśniono, jak można używać typów i członków w <xref:System.Resources> przestrzeni nazw do pracy z plikami .resx.

 Należy pamiętać, że w tym artykule omówiono Praca z danymi XML (resx) plików, które zawierają zasoby. Aby uzyskać informacje na temat pracy z plikami zasobów binarnych, które zostały osadzone w zestawach, zobacz <xref:System.Resources.ResourceManager> tematu.

> [!WARNING]
> Istnieją również sposoby pracy z plikami .resx innych niż programowo. Po dodaniu pliku zasobu do [programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) projektu, Visual Studio udostępnia interfejs do tworzenia i obsługi plików resx i automatycznie służy do konwertowania pliku ResX na plik Resources w czasie kompilacji. Umożliwia także edytora tekstu do modyfikowania pliku ResX bezpośrednio. Jednak aby uniknąć uszkodzenia pliku, należy zachować ostrożność nie należy modyfikować informacje binarne, które są przechowywane w pliku.

## <a name="create-a-resx-file"></a>Utwórz plik Resx

Możesz użyć <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> klasy w celu utworzenia pliku ResX programowo, wykonując następujące czynności:

1.  Utwórz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu przez wywołanie metody <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> metody i podając nazwę pliku resx. Nazwa pliku musi zawierać rozszerzenie resx. W przypadku tworzenia wystąpienia <xref:System.Resources.ResXResourceWriter> obiektu `using` bloku, nie masz jawnie wywołać <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody w kroku 3.

2.  Wywołaj <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody dla każdego zasobu, które chcesz dodać do pliku. Użyj przeciążenia tej metody, aby dodać ciąg, obiekt i danych binarnych (tablicę bajtów). Jeśli zasób jest obiektem, muszą podlegać serializacji.

3.  Wywołaj <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody, aby wygenerować plik zasobów i zwolnić wszystkie zasoby. Jeśli <xref:System.Resources.ResXResourceWriter> obiekt został utworzony w ramach `using` bloku zasobów są zapisywane w pliku ResX i zasoby używane przez <xref:System.Resources.ResXResourceWriter> obiektu są wydawane na końcu `using` bloku.

Wynikowy plik Resx zawiera odpowiedniego nagłówka i `data` tag dla każdego zasobu dodane przez <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.

> [!WARNING]
> Nie używaj plików zasobów do przechowywania haseł, informacje dotyczące zabezpieczeń lub dane prywatne.

Poniższy przykład tworzy plik Resx, o nazwie CarResources.resx, która przechowuje sześć ciągów, ikona i dwa obiekty zdefiniowane przez aplikację (dwa `Automobile` obiektów). Należy pamiętać, że `Automobile` klasy, która jest zdefiniowana, a tworzone w przykładzie, jest oznaczane <xref:System.SerializableAttribute> atrybutu.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Można również użyć [programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) do tworzenia plików resx. W czasie kompilacji program Visual Studio używa [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) Aby przekonwertować plik Resx na zasób binarny (.resources) pliku, a także osadzenie go w zestawie aplikacji lub zestawu satelickiego.

Nie można osadzić pliku resx w pliku wykonywalnym środowiska uruchomieniowego lub wkompilować ją w zestawie satelickim. Należy przekonwertować plik Resx do pliku binarnego (.resources) przy użyciu [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Wynikowy plik Resources, następnie mogą być osadzone w zestawie aplikacji lub zestawu satelickiego. Aby uzyskać więcej informacji, zobacz [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Wyliczanie zasobów
 W niektórych przypadkach można pobrać wszystkie zasoby, zamiast określonego zasobu z pliku resx. Aby to zrobić, można użyć <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> klasy, która zawiera moduł wyliczający dla wszystkich zasobów w pliku resx. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Klasy implementuje <xref:System.Collections.IDictionaryEnumerator>, co powoduje zwrócenie <xref:System.Collections.DictionaryEntry> obiekt, który reprezentuje określony zasób dla każdej iteracji pętli. Jego <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> właściwość zwraca klucz zasobu i jego <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> właściwość zwraca wartość zasobu.

 Poniższy przykład tworzy <xref:System.Resources.ResXResourceReader> obiektu pliku CarResources.resx utworzonego w poprzednim przykładzie i wykonuje iterację przez plik zasobów. Dodaje dwa `Automobile` obiekty, które są zdefiniowane w pliku zasobów <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiektu który dodaje pięć sześć ciągów w celu <xref:System.Collections.SortedList> obiektu. Wartości w <xref:System.Collections.SortedList> obiektu są konwertowane na tablicy parametrów, który jest używany do wyświetlania nagłówki kolumn do konsoli. `Automobile` Wartości właściwości są również wyświetlane w konsoli.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Pobrać określonego zasobu
 Oprócz wyliczanie elementów w pliku ResX, można pobrać określonego zasobu według nazwy, za pomocą <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> klasy. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Metoda pobiera wartość zasób w postaci ciągu o nazwie. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Metoda pobiera wartość nazwanego obiektu lub dane binarne. Metoda zwraca obiekt, który następnie można rzutować (w C#) lub przekonwertować (w języku Visual Basic) do obiektu odpowiedniego typu.

 Poniższy przykład pobiera ciągiem podpisu i ikona według ich nazw zasobów. Również pobierany przez aplikację `Automobile` obiekty używane w poprzednim przykładzie i wyświetla je w <xref:System.Windows.Forms.DataGridView> kontroli.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>Konwertuj pliki resx na pliki binarne Resources
 Konwertowanie plików resx na pliki zasobów osadzonych binarne (Resources) zapewnia znaczące korzyści. Pliki resx są łatwe do odczytu i obsługi podczas tworzenia aplikacji, są one dołączone rzadko gotowe aplikacje. Jeśli rozpowszechniane za pomocą aplikacji istnieje jako oddzielne pliki oprócz plik wykonywalny aplikacji i jej towarzyszącej biblioteki. Z kolei plików Resources są osadzone w pliku wykonywalnym aplikacji lub jej towarzyszący zestawów. Ponadto w przypadku zlokalizowanych aplikacji, opierając się na pliki resx w czasie wykonywania miejscach odpowiedzialność za obsługę zasobów rezerwowej na dewelopera. Z kolei Jeśli zbiór zestawów satelickich, które zawierają pliki Resources osadzonego został utworzony, środowisko uruchomieniowe języka wspólnego obsługuje proces bazowy zasobu.

 Aby przekonwertować plik Resx na plik Resources, należy użyć [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), który ma podstawowe następującą składnię:

 **Resgen.exe** *.resxFilename*

 Wynik jest plik binarny zasobów, która ma taką samą nazwę pliku głównego jako plik .resx i rozszerzenie pliku Resources. Następnie ten plik może być kompilowane w plik wykonywalny lub bibliotekę w czasie kompilacji. Jeśli używasz kompilator Visual Basic można osadzić pliku .resources w pliku wykonywalnym aplikacji należy użyć następującej składni:

 **vbc** *filename* **.vb-resource:** *.resourcesFilename*

 Jeśli używasz C#, składnia jest następująca:

 **CSC** *filename* **.cs-resource:** *.resourcesFilename*

 Plik Resources również mogą być osadzone w zestawie satelickim przy użyciu [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), który ma podstawowe następującą składnię:

 **Al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Zobacz także
- [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)
- [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)
