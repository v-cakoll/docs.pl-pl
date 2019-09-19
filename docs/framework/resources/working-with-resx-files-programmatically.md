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
ms.openlocfilehash: 7e5a57664c5d86ebf394ce026608be9a55872eb8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045536"
---
# <a name="working-with-resx-files-programmatically"></a>Programistyczne praca z plikami. resx
Ponieważ pliki zasobów XML (. resx) muszą zawierać dobrze zdefiniowane dane XML, włącznie z nagłówkiem, który musi być zgodny z określonym schematem, a następnie danymi w parach nazwa/wartość, może się okazać, że ręczne tworzenie tych plików jest podatne na błędy. Alternatywnie można tworzyć pliki resx programowo przy użyciu typów i elementów członkowskich w bibliotece klas .NET. Można również użyć biblioteki klas .NET do pobierania zasobów, które są przechowywane w plikach resx. W tym temacie wyjaśniono, jak można używać typów i elementów członkowskich <xref:System.Resources> w przestrzeni nazw do pracy z plikami. resx.

 Należy zauważyć, że w tym artykule omówiono pracę z plikami XML (. resx) zawierającymi zasoby. Informacje o pracy z plikami zasobów binarnych, które zostały osadzone w zestawach, znajdują się <xref:System.Resources.ResourceManager> w temacie.

> [!WARNING]
> Istnieją również metody pracy z plikami resx innym niż programowe. Po dodaniu pliku zasobów do projektu programu [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) program Visual Studio udostępnia interfejs do tworzenia i obsługi pliku resx oraz automatycznie konwertuje plik resx na plik resources w czasie kompilacji. Można również użyć edytora tekstu do bezpośredniego manipulowania plikiem resx. Jednak aby uniknąć uszkodzenia pliku, należy zachować ostrożność, aby nie modyfikować żadnych informacji binarnych, które są przechowywane w pliku.

## <a name="create-a-resx-file"></a>Utwórz plik resx

Można użyć <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> klasy do programistycznego tworzenia pliku. resx, wykonując następujące czynności:

1. Utworzenie wystąpienia <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> obiektu przez wywołanie metody i podanie nazwy pliku resx. <xref:System.Resources.ResXResourceWriter> Nazwa pliku musi zawierać rozszerzenie resx. Jeśli utworzysz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu `using` w bloku, nie musisz <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> jawnie wywołać metody w kroku 3.

2. Wywołaj <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metodę dla każdego zasobu, który chcesz dodać do pliku. Użyj przeciążenia tej metody, aby dodać dane typu String, Object i binary (tablicę bajtową). Jeśli zasób jest obiektem, musi być możliwy do serializacji.

3. Wywołaj <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metodę w celu wygenerowania pliku zasobów i zwolnienia wszystkich zasobów. Jeśli obiekt został utworzony `using` w bloku, zasoby są zapisywane w pliku resx, a zasoby używane przez <xref:System.Resources.ResXResourceWriter> `using` obiekt są uwalniane na końcu bloku. <xref:System.Resources.ResXResourceWriter>

Otrzymany plik resx ma odpowiedni nagłówek i `data` tag dla każdego zasobu dodanego <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> przez metodę.

> [!WARNING]
> Nie należy używać plików zasobów do przechowywania haseł, informacji o zabezpieczeniach ani danych prywatnych.

Poniższy przykład tworzy plik resx o nazwie CarResources. resx, który przechowuje sześć ciągów, ikonę i dwa obiekty zdefiniowane przez aplikację (dwa `Automobile` obiekty). Należy zauważyć, `Automobile` że Klasa, która jest zdefiniowana i tworzona w przykładzie, jest oznaczona <xref:System.SerializableAttribute> przy użyciu atrybutu.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Możesz również użyć [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) do tworzenia plików resx. W czasie kompilacji program Visual Studio używa [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) , aby przekonwertować plik. resx do pliku zasobów binarnych (. resources), a także osadzić go w zestawie aplikacji lub w zestawie satelickim.

Nie można osadzić pliku resx w pliku wykonywalnym środowiska uruchomieniowego lub skompilować go do zestawu satelickiego. Plik. resx należy skonwertować do pliku zasobów binarnych (. resources) przy użyciu [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md). Utworzony plik resources może następnie zostać osadzony w zestawie aplikacji lub w zestawie satelickim. Aby uzyskać więcej informacji, zobacz [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Wyliczanie zasobów
 W niektórych przypadkach możesz chcieć pobrać wszystkie zasoby, zamiast określonego zasobu, z pliku resx. W tym celu można użyć <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> klasy, która dostarcza moduł wyliczający dla wszystkich zasobów w pliku resx. Klasa implementuje <xref:System.Collections.IDictionaryEnumerator>, która zwraca <xref:System.Collections.DictionaryEntry> obiekt reprezentujący określony zasób dla każdej iteracji pętli. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Jej <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> Właściwość zwraca klucz zasobu, a jej <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> Właściwość zwraca wartość zasobu.

 Poniższy przykład tworzy <xref:System.Resources.ResXResourceReader> obiekt dla pliku CarResources. resx utworzonego w poprzednim przykładzie i wykonuje iterację w pliku zasobów. Dodaje dwa `Automobile` obiekty, które są zdefiniowane w pliku zasobów <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> do obiektu i dodaje pięć z sześciu ciągów do <xref:System.Collections.SortedList> obiektu. Wartości w <xref:System.Collections.SortedList> obiekcie są konwertowane na tablicę parametrów, która jest używana do wyświetlania nagłówków kolumn w konsoli. Wartości `Automobile` właściwości są również wyświetlane w konsoli programu.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Pobieranie określonego zasobu
 Oprócz wyliczania elementów w pliku resx można pobrać konkretny zasób według nazwy przy użyciu <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> klasy. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Metoda pobiera wartość nazwanego zasobu ciągu. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Metoda pobiera wartość nazwanego obiektu lub dane binarne. Metoda zwraca obiekt, który musi następnie być rzutowany (w C#) lub przekonwertowany (w Visual Basic) do obiektu odpowiedniego typu.

 Poniższy przykład pobiera ciąg podpisów formularza i ikony według ich nazw zasobów. Pobiera również obiekty zdefiniowane `Automobile` przez aplikację używane w poprzednim przykładzie i wyświetla je <xref:System.Windows.Forms.DataGridView> w kontrolce.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>Konwertuj pliki resx na pliki binarne. resources
 Konwertowanie plików resx na osadzone pliki zasobów binarnych (. resources) ma znaczące zalety. Chociaż pliki resx są łatwo odczytywane i utrzymywane podczas tworzenia aplikacji, są one rzadko uwzględniane w gotowych aplikacjach. Jeśli są one dystrybuowane z aplikacją, istnieją one jako osobne pliki oprócz pliku wykonywalnego aplikacji i jego dołączonych bibliotek. Z kolei pliki resources są osadzone w pliku wykonywalnym aplikacji lub w jego dołączonych zestawach. Ponadto w przypadku zlokalizowanych aplikacji polegają na plikach resx w czasie wykonywania, które są odpowiedzialne za obsługę powrotu zasobów dla deweloperów. W przeciwieństwie do tego, czy zestaw zestawów satelickich zawierający osadzony plik resources został utworzony, środowisko uruchomieniowe języka wspólnego obsługuje proces rezerwowy zasobu.

 Aby skonwertować plik. resx do pliku Resources, należy użyć [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md), który ma następującą składnię podstawową:

 **Resgen.exe** *.resxFilename*

 Wynikiem jest plik zasobów binarnych, który ma taką samą nazwę pliku głównego jak plik resx i rozszerzenie pliku Resources. Ten plik można następnie skompilować do pliku wykonywalnego lub biblioteki w czasie kompilacji. Jeśli używasz kompilatora Visual Basic, użyj następującej składni, aby osadzić plik resources w pliku wykonywalnym aplikacji:

 **VBC** *Nazwa pliku* **. vb — zasób:** *. resourcesFilename*

 Jeśli używasz C#programu, składnia jest następująca:

 **CSC** *Nazwa pliku* **. cs — zasób:** *. resourcesFilename*

 Plik resources może być również osadzony w zestawie satelitarnym za pomocą [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md), który ma następującą składnię podstawową:

 **Al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Zobacz także

- [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (generator pliku zasobów)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (konsolidator zestawów)](../tools/al-exe-assembly-linker.md)
