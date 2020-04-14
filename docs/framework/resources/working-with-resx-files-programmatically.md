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
ms.openlocfilehash: 3b84d77e4ac9b9889d1bc2f08e5ead6b81deecb0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243040"
---
# <a name="work-with-resx-files-programmatically"></a>Praca programistyczna z plikami .resx

Ponieważ pliki zasobów XML (resx) muszą składać się z dobrze zdefiniowanego pliku XML, w tym nagłówka, który musi być zgodny z określonym schematem, po którym następują dane w parach nazwa/wartość, może się okazać, że ręczne tworzenie tych plików jest podatne na błędy. Alternatywnie można tworzyć pliki .resx programowo przy użyciu typów i elementów członkowskich w bibliotece klas .NET. Biblioteka klas .NET służy również do pobierania zasobów przechowywanych w plikach .resx. W tym artykule wyjaśniono, jak <xref:System.Resources> można używać typów i członków w obszarze nazw do pracy z plikami .resx.

W tym artykule omówiono pracę z plikami XML (resx), które zawierają zasoby. Aby uzyskać informacje na temat pracy z plikami zasobów <xref:System.Resources.ResourceManager>binarnych, które zostały osadzone w zestawach, zobacz .

> [!WARNING]
> Istnieją również sposoby pracy z plikami .resx innymi niż programowo. Po dodaniu pliku zasobów do projektu [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) program Visual Studio udostępnia interfejs do tworzenia i utrzymywania pliku .resx i automatycznie konwertuje plik .resx na plik .resources w czasie kompilacji. Można również użyć edytora tekstu do bezpośredniego manipulowania plikiem .resx. Jednak aby uniknąć uszkodzenia pliku, należy uważać, aby nie modyfikować żadnych informacji binarnych, które są przechowywane w pliku.

## <a name="create-a-resx-file"></a>Tworzenie pliku resx

Klasy można <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> użyć do programowego utworzenia pliku resx, wykonując następujące kroki:

1. Tworzenie wystąpienia <xref:System.Resources.ResXResourceWriter> obiektu przez <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29> wywołanie metody i podanie nazwy pliku .resx. Nazwa pliku musi zawierać rozszerzenie .resx. Jeśli wystąpienia <xref:System.Resources.ResXResourceWriter> obiektu w `using` bloku, nie jawnie trzeba wywołać <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metodę w kroku 3.

2. Wywołanie <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody dla każdego zasobu, który chcesz dodać do pliku. Przeciążenia tej metody można dodać dane ciągu, obiektu i tablicy binarnej (bajtów). Jeśli zasób jest obiektem, musi być serializable.

3. Wywołanie <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody, aby wygenerować plik zasobu i zwolnić wszystkie zasoby. Jeśli <xref:System.Resources.ResXResourceWriter> obiekt został utworzony `using` w bloku, zasoby są zapisywane w pliku .resx, a zasoby używane przez <xref:System.Resources.ResXResourceWriter> obiekt są zwalniane na końcu `using` bloku.

Wynikowy plik .resx ma odpowiedni `data` nagłówek i tag dla <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> każdego zasobu dodanego przez metodę.

> [!WARNING]
> Nie należy używać plików zasobów do przechowywania haseł, informacji poufnych zabezpieczeń ani danych prywatnych.

Poniższy przykład tworzy plik .resx o nazwie CarResources.resx, który przechowuje sześć ciągów, ikonę i dwa obiekty zdefiniowane przez aplikację (dwa `Automobile` obiekty). Klasa, `Automobile` która jest zdefiniowana i wystąpienia w przykładzie, <xref:System.SerializableAttribute> jest oznaczony atrybutem.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Za pomocą [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) można również tworzyć pliki .resx. W czasie kompilacji program Visual Studio używa [generatora plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) do konwersji pliku .resx na plik zasobu binarnego (.resources), a także osadza go w zestawie aplikacji lub zestawie satelickiego.

Nie można osadzić pliku .resx w pliku wykonywalnym środowiska wykonawczego ani skompilować go do zestawu satelickiego. Plik resx należy przekonwertować na plik zasobu binarnego (zasoby) przy użyciu [generatora plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md). Wynikowy plik .resources można następnie osadzać w zestawie aplikacji lub zestawie satelicie. Aby uzyskać więcej informacji, zobacz [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Wyliczaj zasoby
 W niektórych przypadkach można pobrać wszystkie zasoby zamiast określonego zasobu z pliku .resx. Aby to zrobić, można <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> użyć klasy, która zapewnia wyliczenia dla wszystkich zasobów w pliku .resx. Klasa <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> implementuje <xref:System.Collections.IDictionaryEnumerator>, który <xref:System.Collections.DictionaryEntry> zwraca obiekt, który reprezentuje określonego zasobu dla każdej iteracji pętli. Jego <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> właściwość zwraca klucz zasobu, a jego <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> właściwość zwraca wartość zasobu.

 Poniższy przykład <xref:System.Resources.ResXResourceReader> tworzy obiekt dla pliku CarResources.resx utworzonego w poprzednim przykładzie i iteruje za pośrednictwem pliku zasobów. Dodaje dwa `Automobile` obiekty, które są zdefiniowane <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> w pliku zasobów do obiektu i dodaje <xref:System.Collections.SortedList> pięć z sześciu ciągów do obiektu. Wartości w <xref:System.Collections.SortedList> obiekcie są konwertowane na tablicę parametrów, która służy do wyświetlania nagłówków kolumn w konsoli. Wartości `Automobile` właściwości są również wyświetlane w konsoli.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Pobieranie określonego zasobu
 Oprócz wyliczania elementów w pliku .resx, można pobrać określonego zasobu <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> według nazwy przy użyciu klasy. Metoda <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> pobiera wartość zasobu nazwanego ciągu. Metoda <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> pobiera wartość nazwanego obiektu lub danych binarnych. Metoda zwraca obiekt, który następnie musi być rzutowany (w języku C#) lub przekonwertowany (w języku Visual Basic) na obiekt odpowiedniego typu.

 Poniższy przykład pobiera ciąg podpisu formularza i ikonę według ich nazw zasobów. Pobiera również obiekty zdefiniowane `Automobile` przez aplikację używane w poprzednim <xref:System.Windows.Forms.DataGridView> przykładzie i wyświetla je w formancie.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>Konwertowanie plików .resx na binarne pliki .resources
 Konwersja plików .resx na osadzone pliki zasobów binarnych (.resources) ma znaczące zalety. Chociaż pliki .resx są łatwe do odczytania i konserwacji podczas tworzenia aplikacji, rzadko są dołączone do gotowych aplikacji. Jeśli są one dystrybuowane z aplikacją, istnieją one jako oddzielne pliki oprócz pliku wykonywalnego aplikacji i towarzyszących jej bibliotek. Natomiast pliki .resources są osadzone w pliku wykonywalnym aplikacji lub towarzyszących mu zestawach. Ponadto w przypadku zlokalizowanych aplikacji poleganie na plikach .resx w czasie wykonywania nakłada na dewelopera odpowiedzialność za obsługę rezerwowego zasobu. Natomiast jeśli utworzono zestaw zestawów satelickich zawierających osadzone pliki .resources, środowisko wykonawcze języka wspólnego obsługuje proces rezerwowy zasobów.

 Aby przekonwertować plik resx na plik .resources, należy użyć [generatora plików zasobów (Resgen.exe),](../tools/resgen-exe-resource-file-generator.md)który ma następującą podstawową składnię:

 **Resgen.exe** *.resxFilename*

 Wynikiem jest plik zasobów binarnych o takiej samej nazwie pliku głównego jak plik resx i rozszerzenie pliku .resources. Ten plik można następnie skompilować do pliku wykonywalnego lub biblioteki w czasie kompilacji. Jeśli używasz kompilatora języka Visual Basic, użyj następującej składni, aby osadzić plik .resources w pliku wykonywalnym aplikacji:

 nazwa *pliku* **vbc** **.vb -resource:** *.resourcesFilename*

 Jeśli używasz języka C#, składnia jest następująca:

 nazwa *pliku* **csc** **.cs -resource:** *.resourcesFilename*

 Plik .resources można również osadzać w zestawie satelicie za pomocą [łącza montażowego (AL.exe),](../tools/al-exe-assembly-linker.md)który ma następującą podstawową składnię:

 **al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Zobacz też

- [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md)
- [Program Resgen.exe (generator plików zasobów)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (Łącznik montażowy)](../tools/al-exe-assembly-linker.md)
