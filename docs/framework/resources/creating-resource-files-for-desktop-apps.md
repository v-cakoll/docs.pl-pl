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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7ff34285220fd1e3c17503a8387104e91ec08b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313661"
---
# <a name="create-resource-files-for-net-apps"></a>Tworzenie plików zasobów dla aplikacji .NET

W plikach zasobów, aby były łatwo dostępne dla aplikacji, może zawierać zasoby, takie jak ciągi, obrazy lub dane obiektu. .NET Framework oferuje pięć metod tworzenia plików zasobów:

- Utwórz plik tekstowy, który zawiera zasoby w postaci ciągów. Możesz użyć [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do konwertowania pliku tekstowego do pliku binarnego (.resources). Następnie można osadzać pliku binarnego w pliku wykonywalnego aplikacji lub biblioteki aplikacji przy użyciu kompilatora języka lub osadzić w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz [zasoby w plikach tekstowych](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) sekcji.

- Utwórz plik zasobów (.resx) XML, który zawiera ciąg, obrazu lub danych obiektu. Możesz użyć [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) Aby przekonwertować plik Resx na plik binarny zasobów (.resources). Następnie można osadzać pliku binarnego w pliku wykonywalnego aplikacji lub biblioteki aplikacji przy użyciu kompilatora języka lub osadzić w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz [zasoby w plikach resx](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) sekcji.

- Programistyczne tworzenie pliku zasobów (.resx) XML przy użyciu typów w <xref:System.Resources> przestrzeni nazw. Można utworzyć pliku ResX, wyliczanie jej zasoby i pobierania określonych zasobów według nazwy. Aby uzyskać więcej informacji, zobacz temat [Praca z programowo plików resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md).

- Programistyczne tworzenie pliku binarnego (.resources). Następnie można osadzać plik wykonywalny aplikacji lub biblioteki aplikacji przy użyciu kompilatora języka lub osadzić w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz [zasoby w plikach Resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) sekcji.

- Użyj [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) do tworzenia pliku zasobów i umieścić go w swoim projekcie. Visual Studio zawiera Edytor zasobów, która umożliwia dodawanie, usuwanie i modyfikowanie zasobów. W czasie kompilacji pliku zasobów jest automatycznie konwertowany do binarnego pliku Resources i osadzone w zestawie aplikacji lub zestawie satelickim. Aby uzyskać więcej informacji, zobacz [pliki zasobów w programie Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) sekcji.

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Zasoby w plikach tekstowych

Pliki tekstowe (txt lub restext) służy do przechowywania tylko zasoby w postaci ciągów. Dla zasobów niebędących ciągami należy użyć plików resx lub programistycznym tworzeniu. Pliki tekstowe zawierające zasoby w postaci ciągów mają następujący format:

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

 Format pliku zasobów plików txt i restext jest identyczny. Rozszerzenie restext służy jedynie się plikami tekstowymi natychmiastowe określenie jako pliki zasobów w formacie tekstowym.

 Zasoby ciągów są wyświetlane jako *nazwa/wartość* pary, gdzie *nazwa* jest ciągiem, który identyfikuje zasób i *wartość* jest ciągu zasobu, który jest zwracany, jeśli przekazujesz *nazwa* metody pobierania zasobów, takich jak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *Nazwa* i *wartość* muszą być rozdzielone znakiem równości (=). Na przykład:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Nie używaj plików zasobów do przechowywania haseł, informacje dotyczące zabezpieczeń lub dane prywatne.

 Puste ciągi (oznacza to, zasób, którego wartością jest <xref:System.String.Empty?displayProperty=nameWithType>) są dozwolone w plikach tekstowych. Na przykład:

```
EmptyString=
```

 Uruchamianie przy użyciu programu .NET Framework 4.5 i we wszystkich wersjach programu .NET Core, pliki tekstowe obsługują kompilacji warunkowej przy użyciu `#ifdef` *symbol*... `#endif` i `#if !` *symbol*... `#endif` konstrukcji. Następnie można użyć `/define` przełącznik z [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) zdefiniować symbole. Każdy zasób wymaga własnej `#ifdef` *symbol*... `#endif` lub `#if !` *symbol*... `#endif` konstruowania. Jeśli używasz `#ifdef` instrukcji i *symbol* jest zdefiniowany, skojarzony zasób znajduje się w pliku Resources; w przeciwnym razie nie jest on dołączony. Jeśli używasz `#if !` instrukcji i *symbol* jest niezdefiniowana, skojarzony zasób znajduje się w pliku Resources; w przeciwnym razie nie jest on dołączony.

 Komentarze są elementami opcjonalnymi na pliki tekstowe i są poprzedzone znakiem średnika (;) lub znakiem krzyżyk (#) na początku wiersza. Wiersze zawierające komentarze można umieścić w dowolnym miejscu w pliku. Komentarze nie są uwzględnione w pliku .resources skompilowane, który jest tworzony przy użyciu [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Wszelkie puste wiersze w plikach tekstowych są traktowane jako biały znak i są ignorowane.

 W poniższym przykładzie zdefiniowano dwa zasoby w postaci ciągów o nazwie `OKButton` i `CancelButton`.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Jeśli plik tekstowy zawiera zduplikowane wystąpienia *nazwa*, [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) wyświetla ostrzeżenie i zignoruje Nazwa drugiego.

 *wartość* nie może zawierać znaków nowego wiersza, ale można użyć znaków ucieczki w stylu języka C, takich jak `\n` do reprezentowania znakiem nowego wiersza i `\t` do reprezentowania na karcie. Możesz również uwzględnić znak ukośnika odwrotnego, jeśli została ona zmieniona (na przykład "\\\\"). Ponadto dozwolone jest ciągiem pustym.

 Zasoby należy zapisać w formacie pliku tekstowego przy użyciu kodowania UTF-8 lub UTF-16 kodowania w obu kolejności bajtów little-endian lub big-endian. Jednak [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), który służy do konwertowania pliku txt plikiem Resources traktuje pliki jako UTF-8, domyślnie. Jeśli chcesz, aby Resgen.exe rozpoznawanie plików, które zostały zakodowane przy użyciu UTF-16, musi zawierać znacznika kolejności bajtów Unicode (U + FEFF) na początku pliku.

 Aby osadzić pliku zasobów w formacie tekstowym, w ramach zestawu .NET, należy przekonwertować plik do pliku binarnego (.resources) przy użyciu [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Można osadzić pliku .resources w zestawie .NET przy użyciu kompilatora języka lub osadzenie go w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

 W poniższym przykładzie użyto pliku zasobów w formacie tekstowym o nazwie GreetingResources.txt dla prostej aplikacji konsoli "Hello World". Plik tekstowy definiuje dwa ciągi `prompt` i `greeting`, który monituje użytkownika o wpisz jej nazwę i wyświetlić pozdrowienia.

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

Plik tekstowy jest konwertowany na plik Resources przy użyciu następującego polecenia:

```console
resgen GreetingResources.txt
```

 Poniższy przykład zawiera kod źródłowy dla aplikacji konsoli, która używa pliku Resources umożliwiające wyświetlanie komunikatów dla użytkownika.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Jeśli używasz języka Visual Basic i pliku z kodem źródłowym nosi nazwę Greeting.vb, następujące polecenie tworzy plik wykonywalny, który zawiera plik Resources osadzonego:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Jeśli używasz C#i pliku z kodem źródłowym nosi nazwę Greeting.cs, następujące polecenie tworzy plik wykonywalny, który zawiera plik Resources osadzonego:

 ```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>Zasoby w plikach resx
 W przeciwieństwie do plików tekstowych, które można przechowywać tylko zasoby w postaci ciągów, pliki zasobów (.resx) XML można przechowywać ciągów, dane binarne, takie jak obrazy, ikony i klipów audio i obiekty programowe. Plik Resx zawiera standardowy nagłówek, opis formatu wpisy zasobu, która określa informacji o wersji dla formatu XML, który służy do analizowania danych. Dane pliku zasobu poniżej nagłówka XML. Każdy element danych składa się z pary nazwa/wartość, która jest zawarta w `data` tagu. Jego `name` atrybut definiuje nazwę zasobu i zagnieżdżonego `value` tag zawiera wartość zasobu. W przypadku danych ciągu `value` tag zawiera ciąg.

 Na przykład następująca `data` tag definiuje zasób w postaci ciągu o nazwie `prompt` o wartości "wpisz swoje imię:".

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Nie używaj plików zasobów do przechowywania haseł, informacje dotyczące zabezpieczeń lub dane prywatne.

 W przypadku obiektów zasobów **danych** znacznik obejmuje `type` atrybut, który wskazuje na typ danych zasobu. Dla obiektów, które składają się z danych binarnych `data` tag obejmuje również `mimetype` atrybut, który wskazuje `base64` typ danych binarnych.

> [!NOTE]
> Wszystkie pliki .resx Użyj elementu formatującego serializacji binarnej, aby wygenerować i przeanalizować dane binarne dla określonego typu. Co w efekcie plik Resx może stać się nieprawidłowy, jeśli zmieni się w sposób niezgodny binarny format serializacji obiektu.

 W poniższym przykładzie pokazano plik Resx, który zawiera część <xref:System.Int32> zasobów i obraz mapy bitowej.

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
> Ponieważ pliki resx składa się z poprawnie sformułowany kod XML w wstępnie zdefiniowany format, zaleca się praca z plikami .resx ręcznie, szczególnie w przypadku, gdy pliki resx zawiera zasobów innych niż ciągi. Zamiast tego [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) zapewnia przejrzyste interfejs do tworzenia i manipulowania pliki resx. Aby uzyskać więcej informacji, zobacz [pliki zasobów w programie Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) sekcji. Można również tworzyć i programowo manipulować pliki resx. Aby uzyskać więcej informacji, zobacz [Praca z programowo plików resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>Zasoby w plikach Resources

Możesz użyć <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> klasy programowo utworzyć plik binarny zasobów (.resources) bezpośrednio z kodu. Można również użyć [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do utworzenia pliku Resources z plikiem tekstowym lub plikiem resx. Plik Resources może zawierać danych binarnych (tablic bajtów) oraz dane obiektu oprócz danych ciągu. Programowe tworzenie pliku Resources wymaga wykonania następujących czynności:

1. Utwórz <xref:System.Resources.ResourceWriter> obiektu przy użyciu unikatowej nazwy pliku. Można to zrobić, określając nazwę pliku lub strumienia pliku do <xref:System.Resources.ResourceWriter> konstruktora klasy.

2. Wywoływanie jednego z przeciążeń <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> metody dla każdego nazwanego zasobu można dodać do pliku. Zasób może być ciąg, obiekt lub kolekcję danych binarnych (tablicę bajtów).

3. Wywołaj <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metody, aby zapisać zasoby do pliku i zamknąć <xref:System.Resources.ResourceWriter> obiektu.

> [!NOTE]
> Nie używaj plików zasobów do przechowywania haseł, informacje dotyczące zabezpieczeń lub dane prywatne.

 Poniższy przykład programowo utworzy plik Resources o nazwie CarResources.resources, która przechowuje sześć ciągów, ikona i dwa obiekty zdefiniowane przez aplikację (dwa `Automobile` obiektów). Należy pamiętać, że `Automobile` klasy, która jest zdefiniowana, a tworzone w przykładzie, jest oznaczane <xref:System.SerializableAttribute> atrybut, który pozwala na utrwalone przez program formatujący serializacji binarnej.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 Po utworzeniu pliku Resources, można osadzić go w czasie wykonywania plik wykonywalny lub biblioteka przez kompilator języka `/resource` przełączyć lub osadzenie go w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Pliki zasobów w programie Visual Studio

Po dodaniu pliku zasobu do Twojej [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) projektu, Visual Studio tworzy plik resx w katalogu projektu. Program Visual Studio oferuje edytory zasobów, które umożliwiają dodawanie ciągi, obrazy i obiekty binarne. Ponieważ edytory są przeznaczone do obsługi tylko w przypadku danych statycznych, nie można ich używać do przechowywania obiektów programowych; należy zapisywać dane obiektu do jednej z pliku ResX lub do Resources plików programowo. Aby uzyskać więcej informacji, zobacz [Praca z programowo plików resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md) i [zasoby w plikach Resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) sekcji.

W przypadku dodawania zlokalizowanych zasobów, nadaj im taką samą nazwę pliku głównego, jak głównego pliku zasobów. Należy także określić ich kultury w nazwie pliku. Na przykład jeśli dodasz plik zasobów o nazwie Resources.resx, mogą również utworzyć pliki zasobów o nazwie Resources.en US.resx i Resources.fr-FR.resx, aby pomieścić zlokalizowane zasoby dla języka angielskiego (Stany Zjednoczone) i francuski (Francja) kultur, odpowiednio. Należy również określić kulturę domyślną na swojej aplikacji. Jest to kultura, którego zasoby są używane, jeśli można znaleźć nie zlokalizowane zasoby dla określonej kultury. Aby określić domyślną kulturę, w Eksploratorze rozwiązań w programie Visual Studio, kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie aplikacji, kliknij przycisk **informacje o zestawie**i wybierz odpowiedni język/kulturę w **niezależny od język** listy.

W czasie kompilacji program Visual Studio najpierw konwertuje pliki resx w projekcie do plików zasobów binarnych (.resources) i przechowuje je w podkatalogu projektu *obj* katalogu. Program Visual Studio osadza pliki zasobów, które nie zawierają zlokalizowanych zasobów w głównym zestawie, który jest generowany przez projekt. Jeśli pliki zasobów zawiera zlokalizowane zasoby, Visual Studio umieszcza je w oddzielne zestawy satelickie dla każdej zlokalizowanej kultury. Następnie zapisuje każdy zestaw satelicki w katalogu, którego nazwa odpowiada zlokalizowanej kultury. Na przykład zlokalizowanych zasobów angielski (Stany Zjednoczone) są przechowywane w zestawie satelickim w podkatalogu en US.

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources>
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
- [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
