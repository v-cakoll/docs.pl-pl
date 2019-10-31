---
title: Tworzenie plików zasobów dla aplikacji .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
ms.openlocfilehash: 92e52fb130adecd6acdbeb8eac8d624d3c291094
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129975"
---
# <a name="create-resource-files-for-net-apps"></a>Tworzenie plików zasobów dla aplikacji .NET

Zasoby, takie jak ciągi, obrazy lub dane obiektów, można uwzględnić w plikach zasobów, aby były one łatwo dostępne dla aplikacji. .NET Framework oferuje pięć metod tworzenia plików zasobów:

- Utwórz plik tekstowy, który zawiera zasoby ciągu. Przy użyciu [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) można skonwertować plik tekstowy do pliku zasobów binarnych (Resources). Następnie można osadzić plik zasobów binarnych w pliku wykonywalnym aplikacji lub bibliotece aplikacji przy użyciu kompilatora języka lub osadzić go w zestawie satelitarnym za pomocą [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz sekcję [zasoby w plikach tekstowych](creating-resource-files-for-desktop-apps.md#TextFiles) .

- Utwórz plik zasobów XML (resx), który zawiera ciąg, obraz lub dane obiektu. Przy użyciu [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) można skonwertować plik resx do pliku zasobów binarnych (Resources). Następnie można osadzić plik zasobów binarnych w pliku wykonywalnym aplikacji lub bibliotece aplikacji przy użyciu kompilatora języka lub osadzić go w zestawie satelitarnym za pomocą [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz sekcję [zasoby w plikach resx](creating-resource-files-for-desktop-apps.md#ResxFiles) .

- Utwórz programowo plik zasobów XML (resx) przy użyciu typów w przestrzeni nazw <xref:System.Resources>. Można utworzyć plik resx, wyliczyć jego zasoby i pobrać określone zasoby według nazwy. Więcej informacji znajduje się w temacie [Praca z plikami resx programowo](working-with-resx-files-programmatically.md).

- Utwórz programowo plik zasobów binarnych (Resources). Następnie można osadzić plik w pliku wykonywalnym aplikacji lub bibliotece aplikacji przy użyciu kompilatora języka lub osadzić go w zestawie satelitarnym za pomocą [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz sekcję [Resources in. resources Files](creating-resource-files-for-desktop-apps.md#ResourcesFiles) .

- Użyj [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) , aby utworzyć plik zasobów i uwzględnić go w projekcie. Program Visual Studio udostępnia Edytor zasobów, który pozwala dodawać, usuwać i modyfikować zasoby. W czasie kompilacji plik zasobów jest automatycznie konwertowany na plik binarny. resources i osadzony w zestawie aplikacji lub w zestawie satelickim. Aby uzyskać więcej informacji, zobacz sekcję [pliki zasobów w programie Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) .

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Zasoby w plikach tekstowych

Pliki tekstowe (. txt lub. restext) można używać do przechowywania tylko zasobów ciągu. W przypadku zasobów niebędących ciągami należy używać plików resx lub tworzyć je programowo. Pliki tekstowe zawierające zasoby ciągów mają następujący format:

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 Format pliku zasobów. txt i. restext jest identyczny. Rozszerzenie pliku. restext służy tylko do wprowadzania plików tekstowych, które mają być bezpośrednio identyfikowane jako pliki zasobów tekstowych.

 Zasoby ciągów są wyświetlane jako pary *nazwa/wartość* , gdzie *name* jest ciągiem, który identyfikuje zasób, a *wartość* to ciąg zasobu, który jest zwracany w przypadku przekazania *nazwy* do metody pobierania zasobu, takiej jak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *Nazwa* i *wartość* muszą być rozdzielone znakiem równości (=). Na przykład:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Nie należy używać plików zasobów do przechowywania haseł, informacji o zabezpieczeniach ani danych prywatnych.

 Puste ciągi (czyli zasób, którego wartość jest <xref:System.String.Empty?displayProperty=nameWithType>) są dozwolone w plikach tekstowych. Na przykład:

```text
EmptyString=
```

 Począwszy od .NET Framework 4,5 i we wszystkich wersjach programu .NET Core pliki tekstowe obsługują kompilację warunkową z *symbolem*`#ifdef`... `#endif` i `#if !`*symbol*... `#endif` konstrukcje. Następnie można użyć przełącznika `/define` z [generatorem plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) do definiowania symboli. Każdy zasób wymaga własnego *symbolu*`#ifdef`... `#endif` lub `#if !`*symbol*... `#endif` konstrukcja. Jeśli używasz instrukcji `#ifdef` i *symbol* jest zdefiniowany, skojarzony zasób zostanie uwzględniony w pliku Resources. w przeciwnym razie nie jest uwzględniony. Jeśli używasz instrukcji `#if !` i *symbol* nie jest zdefiniowany, skojarzony zasób zostanie uwzględniony w pliku Resources. w przeciwnym razie nie jest uwzględniony.

 Komentarze są opcjonalne w plikach tekstowych i poprzedzane średnikami (;) lub znakiem krzyżyka (#) na początku wiersza. Wiersze zawierające Komentarze można umieścić w dowolnym miejscu w pliku. Komentarze nie są uwzględniane w skompilowanym pliku Resources, który jest tworzony przy użyciu [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md).

 Wszystkie puste wiersze w plikach tekstowych są uważane za białe znaki i są ignorowane.

 W poniższym przykładzie zdefiniowano dwa zasoby ciągu o nazwie `OKButton` i `CancelButton`.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Jeśli plik tekstowy zawiera zduplikowane wystąpienia *nazwy*, [Generator plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) wyświetla ostrzeżenie i ignoruje drugą nazwę.

 *wartość* nie może zawierać znaków nowego wiersza, ale można użyć znaków ucieczki w stylu języka C, takich jak `\n`, aby reprezentować nowy wiersz i `\t` do reprezentowania karty. Możesz również uwzględnić znak ukośnika odwrotnego, jeśli zostanie on zmieniony (na przykład "\\\\"). Ponadto dozwolony jest pusty ciąg.

 Zasoby należy zapisywać w formacie pliku tekstowego przy użyciu kodowania UTF-8 lub kodowania UTF-16 w kolejności bajtów little-endian lub big-endian. Jednak [Generator plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md), który konwertuje plik txt na plik resources, domyślnie traktuje pliki jako UTF-8. Jeśli chcesz, aby program Resgen. exe rozpoznał plik, który został zakodowany przy użyciu kodowania UTF-16, musisz dołączyć znak kolejności bajtów Unicode (U + FEFF) na początku pliku.

 Aby osadzić plik zasobów w formacie tekstowym w zestawie .NET, należy przekonwertować plik do pliku zasobów binarnych (. resources) przy użyciu [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md). Następnie można osadzić plik resources w zestawie .NET przy użyciu kompilatora języka lub osadzić go w zestawie satelitarnym za pomocą [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md).

 Poniższy przykład używa pliku zasobu w formacie tekstowym o nazwie GreetingResources. txt dla prostej aplikacji konsolowej "Hello world". Plik tekstowy definiuje dwa ciągi, `prompt` i `greeting`, które monitują użytkownika o podanie jego nazwy i wyświetlenie powitania.

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

Plik tekstowy jest konwertowany na plik resources za pomocą następującego polecenia:

```console
resgen GreetingResources.txt
```

 Poniższy przykład pokazuje kod źródłowy aplikacji konsolowej, która używa pliku Resources do wyświetlania komunikatów dla użytkownika.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Jeśli używasz Visual Basic, a plik kodu źródłowego nosi nazwę Greetinging. vb, następujące polecenie tworzy plik wykonywalny zawierający osadzony plik Resources:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Jeśli używasz programu C#, a plik kodu źródłowego ma nazwę Greeting.cs, następujące polecenie tworzy plik wykonywalny zawierający osadzony plik Resources:

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>Zasoby w plikach resx
 W przeciwieństwie do plików tekstowych, które mogą przechowywać tylko zasoby ciągów, pliki zasobów XML (. resx) mogą przechowywać ciągi, dane binarne, takie jak obrazy, ikony i klipy audio i obiekty programistyczne. Plik. resx zawiera standardowy nagłówek, który opisuje format wpisów zasobów i określa informacje o wersji dla pliku XML, który jest używany do analizy danych. Dane pliku zasobu są zgodne z nagłówkiem XML. Każdy element danych składa się z pary nazwa/wartość, które znajdują się w tagu `data`. Jego atrybut `name` definiuje nazwę zasobu, a zagnieżdżony tag `value` zawiera wartość zasobu. W przypadku danych ciągu tag `value` zawiera ciąg.

 Na przykład Poniższy tag `data` definiuje zasób ciągu o nazwie `prompt`, którego wartość to "Wprowadź swoją nazwę:".

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Nie należy używać plików zasobów do przechowywania haseł, informacji o zabezpieczeniach ani danych prywatnych.

 W przypadku obiektów zasobów tag **danych** zawiera atrybut `type`, który wskazuje typ danych zasobu. W przypadku obiektów, które składają się z danych binarnych, tag `data` również zawiera atrybut `mimetype`, który wskazuje `base64` typ danych binarnych.

> [!NOTE]
> Wszystkie pliki RESX używają binarnego programu formatującego serializacji, aby generować i analizować dane binarne dla określonego typu. W związku z tym plik resx może stać się nieprawidłowy, jeśli format serializacji binarnej obiektu zmienia się w niezgodny sposób.

 Poniższy przykład przedstawia część pliku resx, który zawiera zasób <xref:System.Int32> i obraz mapy bitowej.

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> Ponieważ pliki resx muszą zawierać poprawnie sformułowany kod XML w wstępnie zdefiniowanym formacie, nie zaleca się ręcznego pracy z plikami. resx, szczególnie gdy pliki RESX zawierają zasoby inne niż ciągi. Zamiast tego program [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) udostępnia przezroczysty interfejs do tworzenia plików resx i manipulowania nimi. Aby uzyskać więcej informacji, zobacz sekcję [pliki zasobów w programie Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) . Można również programistycznie tworzyć pliki resx i manipulować nimi. Aby uzyskać więcej informacji, zobacz [Praca z plikami resx programowo](working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>Zasoby w plikach. resources

Klasy <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> można użyć do programistycznego tworzenia pliku zasobów binarnych (Resources) bezpośrednio w kodzie. Można również użyć [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) , aby utworzyć plik resources z pliku tekstowego lub resx. Plik resources może zawierać dane binarne (tablice bajtowe) i dane obiektu oprócz danych ciągu. Programowe tworzenie pliku resources wymaga wykonania następujących czynności:

1. Utwórz obiekt <xref:System.Resources.ResourceWriter> z unikatową nazwą pliku. Można to zrobić, określając nazwę pliku lub strumień pliku do konstruktora klasy <xref:System.Resources.ResourceWriter>.

2. Wywołaj jedno z przeciążeń metody <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> dla każdego nazwanego zasobu, aby dodać je do pliku. Zasób może być ciągiem, obiektem lub kolekcją danych binarnych (tablicą bajtową).

3. Wywołaj metodę <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType>, aby zapisać zasoby do pliku i zamknąć obiekt <xref:System.Resources.ResourceWriter>.

> [!NOTE]
> Nie należy używać plików zasobów do przechowywania haseł, informacji o zabezpieczeniach ani danych prywatnych.

 Poniższy przykład programowo tworzy plik resources o nazwie CarResources. resources, który przechowuje sześć ciągów, ikonę i dwa obiekty zdefiniowane przez aplikację (dwa `Automobile` obiekty). Należy zauważyć, że Klasa `Automobile`, która jest zdefiniowana i tworzona w przykładzie, jest oznaczona przy użyciu atrybutu <xref:System.SerializableAttribute>, co umożliwia jego utrwalanie przez program formatujący serializacji binarnej.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 Po utworzeniu pliku Resources można go osadzić w pliku wykonywalnym lub bibliotece środowiska uruchomieniowego, dołączając przełącznik `/resource` kompilatora języka lub osadzić go w zestawie satelitarnym za pomocą [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md).

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Pliki zasobów w programie Visual Studio

Po dodaniu pliku zasobów do projektu programu [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) program Visual Studio tworzy plik resx w katalogu projektu. Program Visual Studio udostępnia edytory zasobów, które umożliwiają dodawanie ciągów, obrazów i obiektów binarnych. Ponieważ edytory są zaprojektowane do obsługi tylko danych statycznych, nie mogą być używane do przechowywania obiektów programistycznych; należy zapisać dane obiektu w pliku resx lub w pliku. resources programowo. Aby uzyskać więcej informacji, zobacz [Praca z plikami resx programowo](working-with-resx-files-programmatically.md) i [w sekcji zasoby w plikach. resources](creating-resource-files-for-desktop-apps.md#ResourcesFiles) .

W przypadku dodawania zlokalizowanych zasobów nadaj im taką samą nazwę pliku głównego jak główny plik zasobów. Należy również wyznaczyć swoją kulturę w nazwie pliku. Na przykład, jeśli dodasz plik zasobów o nazwie Resources. resx, możesz również utworzyć pliki zasobów o nazwie Resources. en-US. resx i Resources.fr-FR. resx, odpowiednio przechowując zlokalizowane zasoby dla kultur angielskiej (Stany Zjednoczone) i francuski (Francja). Należy również wyznaczyć domyślną kulturę aplikacji. Jest to kultura, której zasoby są używane, jeśli nie można znaleźć zlokalizowanych zasobów dla określonej kultury. Aby określić domyślną kulturę, w Eksplorator rozwiązań w programie Visual Studio kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie aplikacja, kliknij pozycję **Informacje o zestawie**i wybierz odpowiedni język/kulturę na liście **języka neutralnego** .

W czasie kompilacji program Visual Studio najpierw konwertuje pliki resx w projekcie na pliki zasobów binarnych (. resources) i zapisuje je w podkatalogu katalogu *obj* projektu. Program Visual Studio osadza wszystkie pliki zasobów, które nie zawierają zlokalizowanych zasobów w zestawie głównym, który jest generowany przez ten projekt. Jeśli jakiekolwiek pliki zasobów zawierają zlokalizowane zasoby, program Visual Studio osadzi je w oddzielnych zestawach satelickich dla każdej zlokalizowanej kultury. Następnie przechowuje każdy zestaw satelicki w katalogu, którego nazwa odpowiada zlokalizowanej kulturze. Na przykład zlokalizowane zasoby w języku angielskim (Stany Zjednoczone) są przechowywane w zestawie satelity w podkatalogu en-US.

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources>
- [Zasoby w aplikacjach klasycznych](index.md)
- [Opakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md)
