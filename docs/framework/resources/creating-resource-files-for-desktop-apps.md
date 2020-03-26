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
ms.openlocfilehash: b679539be1aeb593124eb35a235bcc578decb4c0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111780"
---
# <a name="create-resource-files-for-net-apps"></a>Tworzenie plików zasobów dla aplikacji .NET

Zasoby, takie jak ciągi, obrazy lub dane obiektów, można uwzględnić w plikach zasobów, aby były łatwo dostępne dla aplikacji. Program .NET Framework oferuje pięć sposobów tworzenia plików zasobów:

- Utwórz plik tekstowy zawierający zasoby ciągów. [Generator plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) służy do konwertowania pliku tekstowego na plik zasobu binarnego (.resources). Następnie można osadzić plik zasobów binarnych w pliku wykonywalnym aplikacji lub w bibliotece aplikacji przy użyciu kompilatora języka lub osadzić go w zestawie satelicie za pomocą [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz zasoby [w plikach tekstowych](creating-resource-files-for-desktop-apps.md#TextFiles) sekcji.

- Utwórz plik zasobu XML (resx), który zawiera ciąg, obraz lub dane obiektu. Generator [plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) służy do konwertowania pliku resx na plik zasobu binarnego (.resources). Następnie można osadzić plik zasobów binarnych w pliku wykonywalnym aplikacji lub w bibliotece aplikacji przy użyciu kompilatora języka lub osadzić go w zestawie satelicie za pomocą [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz sekcję [Zasoby w plikach resx.](creating-resource-files-for-desktop-apps.md#ResxFiles)

- Programowo utwórz plik zasobu XML (resx) <xref:System.Resources> przy użyciu typów w obszarze nazw. Można utworzyć plik resx, wyliczyć jego zasoby i pobrać określone zasoby według nazwy. Aby uzyskać więcej informacji, zobacz [Programowo praca z plikami resx](working-with-resx-files-programmatically.md).

- Programowo utwórz plik zasobu binarnego (.resources). Następnie można osadzić plik w pliku wykonywalnym aplikacji lub w bibliotece aplikacji przy użyciu kompilatora języka lub osadzić go w zestawie satelicie za pomocą [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz sekcję [Zasoby w plikach .resources.](creating-resource-files-for-desktop-apps.md#ResourcesFiles)

- Użyj [programu Visual Studio,](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) aby utworzyć plik zasobów i dołączyć go do projektu. Visual Studio udostępnia edytor zasobów, który umożliwia dodawanie, usuwanie i modyfikowanie zasobów. W czasie kompilacji plik zasobu jest automatycznie konwertowany na binarny plik .resources i osadzony w zestawie aplikacji lub zestawie satelicie. Aby uzyskać więcej informacji, zobacz sekcję [Pliki zasobów w programie Visual Studio.](creating-resource-files-for-desktop-apps.md#VSResFiles)

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Zasoby w plikach tekstowych

Pliki tekstowe (.txt lub .restext) można używać do przechowywania tylko zasobów ciągów. W przypadku zasobów innych niż ciągi należy użyć plików resx lub utworzyć je programowo. Pliki tekstowe zawierające zasoby ciągów mają następujący format:

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

 Format pliku zasobów plików .txt i .restext jest identyczny. Rozszerzenie pliku .restext służy jedynie do plików tekstowych natychmiast identyfikowalne jako pliki zasobów tekstowych.

 Zasoby ciągów są wyświetlane jako pary *nazw/wartości,* gdzie *nazwa* jest ciągiem identyfikującym zasób, a *wartością* jest <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>ciąg zasobu zwracany po przedaniu *nazwy* do metody pobierania zasobów, takiej jak . *nazwa* i *wartość* muszą być oddzielone znakiem równości (=). Przykład:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Nie należy używać plików zasobów do przechowywania haseł, informacji poufnych zabezpieczeń ani danych prywatnych.

 Puste ciągi (czyli zasób, <xref:System.String.Empty?displayProperty=nameWithType>którego wartością jest) są dozwolone w plikach tekstowych. Przykład:

```text
EmptyString=
```

 Począwszy od .NET Framework 4.5 i we wszystkich wersjach .NET `#ifdef`Core, pliki tekstowe obsługują kompilację warunkową z *symbolem*... `#endif` i `#if !` *symbol*... `#endif` konstrukcji. Następnie można użyć `/define` przełącznika z [generatorem plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) do definiowania symboli. Każdy zasób `#ifdef`wymaga własnego *symbolu*... `#endif` lub `#if !` *symbol*... `#endif` konstrukcji. Jeśli używana `#ifdef` jest instrukcja i *symbol* jest zdefiniowany, skojarzony zasób jest zawarty w pliku .resources; w przeciwnym razie nie jest uwzględniony. Jeśli używasz `#if !` instrukcji i *symbol* nie jest zdefiniowany, skojarzony zasób jest zawarty w pliku .resources; w przeciwnym razie nie jest uwzględniony.

 Komentarze są opcjonalne w plikach tekstowych i są poprzedzone średnikiem (;) lub przez znak funta (#) na początku wiersza. Wiersze zawierające komentarze można umieścić w dowolnym miejscu w pliku. Komentarze nie są uwzględniane w skompilowanym pliku .resources, który jest tworzony przy użyciu [generatora plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).

 Wszystkie puste wiersze w plikach tekstowych są uważane za białe i są ignorowane.

 Poniższy przykład definiuje dwa `OKButton` zasoby `CancelButton`ciągów o nazwie i .

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Jeśli plik tekstowy zawiera zduplikowane wystąpienia *nazwy,* [generator plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) wyświetla ostrzeżenie i ignoruje drugą nazwę.

 *wartość* nie może zawierać nowych znaków wiersza, ale można `\n` użyć znaków ucieczki w stylu języka C, takich jak reprezentowanie nowego wiersza i `\t` reprezentowanie karty. Można również dołączyć znak ukośnika odwrotnego, jeśli\\\\jest on zmieniony (na przykład " "). Ponadto dozwolony jest pusty ciąg.

 Zapisz zasoby w formacie pliku tekstowego przy użyciu kodowania UTF-8 lub kodowania UTF-16 w kolejności bajtów małotunianych lub big-endian. Jednak [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md), który konwertuje plik txt na plik .resources, domyślnie traktuje pliki jako UTF-8. Jeśli chcesz, aby program Resgen.exe rozpoznał plik zakodowany przy użyciu utf-16, na początku pliku należy dołączyć znacznik kolejności bajtów Unicode (U+FEFF).

 Aby osadzić plik zasobu w formacie tekstowym do zestawu .NET, należy przekonwertować plik na plik zasobu binarnego (zasoby) przy użyciu [generatora plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md). Następnie można osadzić plik .resources w zestawie .NET przy użyciu kompilatora języka lub osadzić go w zestawie satelicie za pomocą [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md).

 W poniższym przykładzie użyto pliku zasobów w formacie tekstowym o nazwie GreetingResources.txt dla prostej aplikacji konsoli "Hello World". Plik tekstowy definiuje dwa `prompt` ciągi znaków, a `greeting`w ten sposób monituje użytkownika o wprowadzenie nazwy i wyświetlenie powitania.

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

Plik tekstowy jest konwertowany na plik .resources za pomocą następującego polecenia:

```console
resgen GreetingResources.txt
```

 W poniższym przykładzie pokazano kod źródłowy aplikacji konsoli, która używa pliku .resources do wyświetlania wiadomości do użytkownika.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Jeśli używasz języka Visual Basic, a plik kodu źródłowego nosi nazwę Greeting.vb, następujące polecenie tworzy plik wykonywalny zawierający osadzony plik .resources:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Jeśli używasz języka C#, a plik kodu źródłowego nosi nazwę Greeting.cs, następujące polecenie tworzy plik wykonywalny zawierający osadzony plik .resources:

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>Zasoby w plikach .resx
 W przeciwieństwie do plików tekstowych, które mogą przechowywać tylko zasoby ciągów, pliki zasobów XML (.resx) mogą przechowywać ciągi, dane binarne, takie jak obrazy, ikony i klipy audio oraz obiekty programowe. Plik .resx zawiera standardowy nagłówek, który opisuje format wpisów zasobów i określa informacje o wersji dla pliku XML używanego do analizowania danych. Dane pliku zasobu są zgodne z nagłówkiem XML. Każdy element danych składa się z pary nazwa/wartość, która jest zawarta w tagu. `data` Jego `name` atrybut definiuje nazwę zasobu, a `value` znacznik zagnieżdżony zawiera wartość zasobu. W przypadku danych `value` ciągu tag zawiera ciąg.

 Na przykład poniższy `data` tag definiuje zasób ciągu o nazwie, `prompt` którego wartość to "Wprowadź swoją nazwę:".

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Nie należy używać plików zasobów do przechowywania haseł, informacji poufnych zabezpieczeń ani danych prywatnych.

 W przypadku obiektów **data** zasobów znacznik `type` danych zawiera atrybut wskazujący typ danych zasobu. Dla obiektów, które składają `data` się z `mimetype` danych binarnych, `base64` tag zawiera również atrybut, który wskazuje typ danych binarnych.

> [!NOTE]
> Wszystkie pliki .resx używają binarnego formatera serializacji do generowania i analizowania danych binarnych dla określonego typu. W rezultacie plik .resx może stać się nieprawidłowy, jeśli format serializacji binarnej obiektu zmieni się w niezgodny sposób.

 W poniższym przykładzie przedstawiono część pliku .resx, która zawiera <xref:System.Int32> zasób i obraz mapy bitowej.

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
> Ponieważ pliki .resx muszą składać się z dobrze sformułowanego formatu XML w predefiniowanym formacie, nie zalecamy ręcznej pracy z plikami .resx, szczególnie gdy pliki .resx zawierają zasoby inne niż ciągi. Zamiast tego [visual studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) udostępnia przejrzysty interfejs do tworzenia i manipulowania plikami .resx. Aby uzyskać więcej informacji, zobacz sekcję [Pliki zasobów w programie Visual Studio.](creating-resource-files-for-desktop-apps.md#VSResFiles) Można również programowo tworzyć pliki .resx i manipulować nimi. Aby uzyskać więcej informacji, zobacz [Programowo praca z plikami resx](working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>Zasoby w plikach .resources

<xref:System.Resources.ResourceWriter?displayProperty=nameWithType> Klasy można użyć do programowego tworzenia pliku zasobu binarnego (.resources) bezpośrednio z kodu. Generator plików [zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) służy również do tworzenia pliku .resources z pliku tekstowego lub pliku resx. Plik .resources może zawierać dane binarne (tablice bajtów) i dane obiektów oprócz danych ciągu. Programowe tworzenie pliku .resources wymaga następujących kroków:

1. Utwórz <xref:System.Resources.ResourceWriter> obiekt o unikatowej nazwie pliku. Można to zrobić, określając nazwę pliku lub strumień plików <xref:System.Resources.ResourceWriter> do konstruktora klasy.

2. Wywołanie jednego z przeciążenia <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> metody dla każdego nazwanego zasobu, aby dodać do pliku. Zasób może być ciągiem, obiektem lub kolekcją danych binarnych (tablica bajtów).

3. Wywołanie <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metody, aby zapisać zasoby do <xref:System.Resources.ResourceWriter> pliku i zamknąć obiekt.

> [!NOTE]
> Nie należy używać plików zasobów do przechowywania haseł, informacji poufnych zabezpieczeń ani danych prywatnych.

 Poniższy przykład programowo tworzy plik .resources o nazwie CarResources.resources, który przechowuje sześć ciągów, ikonę i dwa obiekty zdefiniowane przez aplikację (dwa `Automobile` obiekty). Klasa, `Automobile` która jest zdefiniowana i wystąpienia w przykładzie, <xref:System.SerializableAttribute> jest oznaczony atrybutem, który umożliwia utrwalenie przez formater serializacji binarnej.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 Po utworzeniu pliku .resources można go osadzić w pliku wykonywalnym lub `/resource` bibliotece w czasie wykonywania, dołączając przełącznik kompilatora języka lub osadzać go w zestawie satelicie za pomocą [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md).

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Pliki zasobów w programie Visual Studio

Po dodaniu pliku zasobów do projektu [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) program Visual Studio tworzy plik resx w katalogu projektu. Program Visual Studio udostępnia edytory zasobów, które umożliwiają dodawanie ciągów, obrazów i obiektów binarnych. Ponieważ edytory są przeznaczone do obsługi tylko danych statycznych, nie można ich używać do przechowywania obiektów programowych; należy zapisać dane obiektu w pliku .resx lub w pliku .resources programowo. Aby uzyskać więcej informacji, zobacz [Programowa praca z plikami resx](working-with-resx-files-programmatically.md) i sekcją [Zasoby w plikach .resources.](creating-resource-files-for-desktop-apps.md#ResourcesFiles)

Jeśli dodajesz zlokalizowane zasoby, nadaj im taką samą nazwę pliku głównego jak główny plik zasobu. Należy również wyznaczyć ich kultury w nazwie pliku. Na przykład po dodaniu pliku zasobów o nazwie Resources.resx można również utworzyć pliki zasobów o nazwie Resources.en-US.resx i Resources.fr-FR.resx, aby przechowywać zlokalizowane zasoby odpowiednio dla kultur języka angielskiego (Stany Zjednoczone) i francuskiego (Francja). Należy również wyznaczyć domyślną kulturę aplikacji. Jest to kultura, której zasoby są używane, jeśli nie zlokalizowane zasoby dla określonej kultury można znaleźć. Aby określić kulturę domyślną, w Eksploratorze rozwiązań w programie Visual Studio kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie Aplikacja, kliknij polecenie **Informacje o zestawie**i wybierz odpowiedni język/kulturę na liście Języka **neutralnego.**

W czasie kompilacji program Visual Studio najpierw konwertuje pliki .resx w projekcie na pliki zasobów binarnych (.resources) i przechowuje je w podkatalogu katalogu *obj* projektu. Visual Studio osadza wszystkie pliki zasobów, które nie zawierają zlokalizowanych zasobów w głównym zestawie, który jest generowany przez projekt. Jeśli pliki zasobów zawierają zlokalizowane zasoby, program Visual Studio osadza je w oddzielnych zestawach satelitalnych dla każdej zlokalizowanej kultury. Następnie przechowuje każdy zestaw satelickiego w katalogu, którego nazwa odpowiada zlokalizowane kultury. Na przykład zlokalizowane zasoby języka angielskiego (Stany Zjednoczone) są przechowywane w zestawie satelicie w podkatalogu en-US.

## <a name="see-also"></a>Zobacz też

- <xref:System.Resources>
- [Zasoby w aplikacjach klasycznych](index.md)
- [Opakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md)
