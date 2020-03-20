---
title: Program Winres.exe (Edytor lokalizacji zasobów systemu Windows)
ms.date: 08/15/2018
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- Windows Resource Localization Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
ms.openlocfilehash: 2cfb2d9874b34eef78fe462e0270fd70307a9f61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715709"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Program Winres.exe (Edytor lokalizacji zasobów systemu Windows)

Edytor lokalizacji zasobów systemu Windows, Winres.exe, to narzędzie układu wizualnego, które pomaga ekspertom lokalizacyjnym zlokalizować zasoby interfejsu użytkownika (UI) formularzy systemu Windows używane przez formularze. Pliki resx lub resources używane jako dane wejściowe do Winres.exe mogą być tworzone przy użyciu środowiska projektowania wizualnego, takiego jak Microsoft Visual Studio. Aby uzyskać informacje na temat wdrażania zasobów w aplikacjach platformy .NET Framework, zobacz [Zasoby w aplikacjach klasycznych](../resources/index.md).

Program Winres.exe jest instalowany w programie Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

## <a name="syntax"></a>Składnia

```console
winres resourceFile
winres /?
```

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`resourceFile`|Plik zasobów do zlokalizowania. Ten plik musi być plikiem resx lub resources formularza Windows Forms wygenerowanym przez projektanta programu Visual Studio. Winres.exe nie może otwierać rodzajowych plików resx i resources.|

|Opcja|Opis|
|------------|-----------------|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

## <a name="remarks"></a>Uwagi

Stan elementów interfejsu użytkownika z formularza w projekcie programu Windows Forms jest zazwyczaj zapisywany w plikach zasobów, które są albo plikami XML z rozszerzeniem resx, lub odpowiednio skompilowanymi wersjami binarnymi z rozszerzeniem resources. Winres.exe jest narzędziem, które umożliwia ograniczone edytowanie obu typów plików poza środowiskiem projektowania programu Visual Studio. W szczególności umożliwia następujące rodzaje operacji edycji:

- Plik zasobów kultury neutralnej lub określonej można edytować, aby zmienić właściwości interfejsu użytkownika formularza lub jego formantów, takich jak ich tekst, rozmiar lub położenie.

- Pliki zasobów kultury neutralnej lub określonej mogą być generowane z domyślnego pliku zasobów.

- Plik zasobów kultury można zapisać jako inny plik zasobów kultury. Na przykład plik zasobów Angielski (USA) można zapisać jako plik zasobów Polski. Zazwyczaj nowy plik będzie można później edytować, aby był zgodny z nową kulturą.

Zobacz też [hierarchiczna organizacja zasobów do lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) lub [hierarchiczna organizacja zasobów dla lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120)).

Winres.exe nie może skonwertować pliku resx na odpowiedni plik resources; użyj narzędzia Resgen.exe. Aby uzyskać więcej informacji na temat pliku Resgen.exe, zobacz [Resgen.exe (Resource File Generator)](resgen-exe-resource-file-generator.md).

Winres.exe jest aplikacją graficzną, która odtwarza wersję formularza Windows Forms czasu projektowania z samego pliku zasobów, bez dostępu do kodu źródłowego. Program Winres.exe obsługuje program Visual Studio **Windows Forms Form Designer** i okno **Właściwości.** Te funkcje umożliwiają wizualne edytowanie pliku resources lub resx zawierającego formularz Windows Forms. Zazwyczaj localizers używać Winres.exe do edycji etykiet kontroli i dostosować lokalizację i rozmiar formantów, aby pomieścić etykiety dla kultury docelowej.

Jeśli Winres.exe nie może rozpoznać typu formantu, utworzy formant zastępczy formantu w zlokalizowanym pliku resources lub resx. Symbol zastępczy formantu pojawia się w formularzu Windows Forms jako okno zakreskowane. Rozmiar i położenie zakreskowanego okna są zgodne z rzeczywistym formantem. Wszystkie dostępne właściwości lokalizowalne dla formantu zastępczego są wyświetlane w oknie **Właściwości.** Wszelkie zmiany wprowadzone do symbolu zastępczego formantu są zapisywane dla rzeczywistego formantu.

## <a name="winresexe-versus-visual-studio"></a>Winres.exe a Visual Studio

Ogólnie rzecz biorąc, przed rozpoczęciem lokalizowania formularzy Windows Forms aplikacji należy zadecydować, czy jako narzędzia do lokalizacji używać programu Visual Studio czy Winres.exe. Zgodność wersji opisana poniżej może uniemożliwić przejście od jednego narzędzia do drugiego.

Zaletą programu Visual Studio jest to, że można za jego pomocą tworzyć i lokalizować aplikacje. Aby zlokalizować formularz, po zakończeniu rozwoju, należy <xref:System.ComponentModel.LocalizableAttribute> ustawić formę **(Localizable** właściwości `true` w edytorze **właściwości)** i zmienić jego **Language** właściwości do żądanej kultury docelowej. Następnie należy przeprowadzić edycję ciągów i dostosować położenie i rozmiar formantów, aby pomieściły ciągi dla kultury docelowej. Podczas zapisywania zlokalizowanego pliku resx Visual Studio zapisuje w pliku tylko lokalizowalne właściwości (właściwości zmienione w docelowej kulturze). Program Visual Studio automatycznie tworzy zestaw satelicki dla zlokalizowanego pliku resx w lokalizacji odpowiedniego katalogu.

Chociaż program Visual Studio zapewnia zintegrowane środowisko programistyczne i lokalizacyjne, program Winres.exe jest zalecanym narzędziem do użycia, jeśli lokalizacja jest wykonywana przez lokalnych firm innych firm. Ponieważ Winres.exe jest tylko narzędziem do lokalizacji, umożliwia jaśniejsze rozdzielenie kodu aplikacji od formularzy, które mają zostać zlokalizowane, co jest praktyczniejsze w przypadku zarządzania dużymi projektami.

## <a name="using-winresexe"></a>Korzystanie z Winres.exe

Aby zlokalizować przy użyciu programu Winres.exe, należy najpierw opracować aplikację przy użyciu projektanta wizualnego, takiego jak **projektant formularzy systemu Windows** w programie Visual Studio. Po zakończeniu rozwoju ustaw formularz <xref:System.ComponentModel.LocalizableAttribute> **(właściwość Localizable** w edytorze `true` **Właściwości)** na , a następnie przekaż plik .resx dla kultury domyślnej do localizatora innej firmy. Ten plik resx zawiera dodatkowe informacje, których Winres.exe używa do odtworzenia wersji oryginalnego formularza z czasu projektowania.

> [!NOTE]
> Programu Winres.exe nie można używać do edytowania domyślnego pliku zasobów. Winres.exe interpretuje wszystkie zmienione właściwości jako właściwości zlokalizowane i zapisuje je do pliku zasobów docelowej kultury.

Ostateczna wersja pliku zasobów kultury może zostać użyta do utworzenia zlokalizowanej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Zasoby w aplikacjach klasycznych](../resources/index.md).

Program Winres.exe oferuje następujące funkcje i możliwości:

- Winres może działać w trybie pojedynczego pliku (SFM) lub w trybie pliku Visual Studio (VSFM). SFM jest starszym trybem, w którym w pliku zasobów są zapisywane pełne informacje o formularzu i jego zawartość. W trybie VSFM w pliku zasobów zapisywane są tylko zmiany dotyczące kultury.

- Okno raportowania błędów, zadokowane do lewego dolnego rogu okna głównego.

- Skróty klawiszowe można sprawdzić pod kątem duplikatów: z menu **Format** kliknij polecenie **Sprawdź skrót klawiszowe.**

## <a name="version-compatibility"></a>Zgodność wersji

Należy użyć wersji programu Winres.exe, która została wydana z programem .NET Framework, którego używasz. W poniższej tabeli wymieniono zgodne wersje:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Program Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2.0|2.0|
|Visual Studio 2008|3.0 i 3.5|3.0 i 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> Chociaż tryb VSFM ma tę zaletę, że jest zgodny z programem Visual Studio, ponieważ są w nim zapisywane tylko zmienione wartości, program Winres.exe wymaga, aby w tym samym katalogu znajdował się pierwotny plik zasobów. Na przykład edycja `TestApp.de-DE.resources`pliku zasobów w języku niemieckim w Niemczech wymaga `TestApp.resx`obecności domyślnego pliku zasobów i `TestApp.de.resources`ewentualnie pliku zasobów neutralnego dla kultury.

## <a name="examples"></a>Przykłady

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Aby zlokalizować plik resx lub .resources skojarzony z formularzem

1. Wpisz `winres` wiersz polecenia dewelopera, aby uruchomić program Winres.exe.

2. Aby otworzyć domyślne zasoby formularza do zlokalizowania, kliknij polecenie **Otwórz** w menu **Plik** i przejdź do pliku, aby go otworzyć.

     — lub —

     Określ plik do otwarcia w wierszu polecenia podczas uruchamiania programu Winres.exe.

     Następujące polecenie uruchamia program Winres.exe i ładuje `TestApp.resx` formularz skojarzony z projektantem formularzy.

    ```console
    winres TestApp.resx
    ```

     Następujące polecenie uruchamia program Winres.exe i ładuje `TestApp.resources` formularz skojarzony z projektantem formularzy.

    ```console
    winres TestApp.resources
    ```

    > [!NOTE]
    > Jeśli formularz, którego zasoby są edytowane, jest odziedziczonym formularzem, zarówno zestaw zawierający formularz, po którym został odziedziczony edytowany formularz, jak i zestaw zawierający dziedziczący formularz muszą być albo zarejestrowane w globalnej pamięci podręcznej zestawów (GAC) lub znajdować się w tym samym katalogu co plik WinRes.exe. Aby uzyskać więcej informacji na temat instalowania składników programu .NET Framework w pamięci podręcznej GAC, zobacz [Globalna pamięć podręczna zestawów](../app-domains/gac.md).

3. Wybierz formanty w <xref:System.Windows.Forms.Control.Text%2A> formularzu i zmień ich i inne właściwości, aby odzwierciedlić zlokalizowaną kulturę i jej język. Przenoszenie lub zmienianie rozmiaru formantów w celu dostosowania zlokalizowanego tekstu.

4. Aby zapisać zlokalizowane wersje pliku .resx lub .resources, kliknij ikonę **Zapisz** lub to samo polecenie w menu **Plik.** Narzędzie wyświetla okno **Wybierz kulturę.**

5. Wybierz odpowiednią kulturę i tryb pliku, a następnie kliknij przycisk **OK**.

   Narzędzie zapisuje plik przy użyciu konwencji nazewnictwa, której oczekuje czas wykonywania dla zlokalizowanych plików zasobów. Na przykład, jeśli `TestApp.resources` lokalizujesz dla języka niemieckiego w `TestApp.de-DE.resources`Niemczech, narzędzie zapisze plik jako . Jeśli lokalizujesz `TestApp.resx` dla języka niemieckiego w Niemczech, `TestApp.de-DE.resx`narzędzie zapisze plik jako . Aby uzyskać więcej informacji na temat konwencji nazewnictwa zasobów, zobacz [Pakowanie i wdrażanie zasobów](../resources/packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać listę wstępnie zdefiniowanych nazw kultury używanych przez <xref:System.Globalization.CultureInfo> czas wykonywania, zobacz klasę.

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [narzędzia](index.md)
- [Zasoby w aplikacjach klasycznych](../resources/index.md)
- [Globalizacja i lokalizacja](../../standard/globalization-localization/index.md)
