---
title: Winres. exe (Edytor lokalizacji zasobów systemu Windows)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df7ce0795daabdf34f46e20460bef23e7c486467
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043905"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres. exe (Edytor lokalizacji zasobów systemu Windows)

Edytor lokalizacji zasobów systemu Windows, Winres. exe, to narzędzie do układu wizualizacji, które ułatwia ekspertom Lokalizowanie Windows Forms zasobów interfejsu użytkownika (UI) używanych w formularzach. Pliki resx lub resources używane jako dane wejściowe do Winres.exe mogą być tworzone przy użyciu środowiska projektowania wizualnego, takiego jak Microsoft Visual Studio. Aby uzyskać informacje na temat wdrażania zasobów w aplikacjach .NET Framework, zobacz [zasoby w aplikacjach klasycznych](../resources/index.md).

Środowisko Winres. exe jest instalowane z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

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

Zapoznaj się również [z hierarchiczną organizacją zasobów dla lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) lub [hierarchicznej organizacji zasobów do lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120)).

Winres.exe nie może skonwertować pliku resx na odpowiedni plik resources; użyj narzędzia Resgen.exe. Aby uzyskać więcej informacji na temat programu Resgen. exe, zobacz [Resgen. exe (Generator plików zasobów)](resgen-exe-resource-file-generator.md).

Winres.exe jest aplikacją graficzną, która odtwarza wersję formularza Windows Forms czasu projektowania z samego pliku zasobów, bez dostępu do kodu źródłowego. Winres. exe hostuje **Windows Forms projektanta formularzy** i **Właściwości** programu Visual Studio. Te funkcje umożliwiają wizualne edytowanie pliku resources lub resx zawierającego formularz Windows Forms. Zazwyczaj lokalizatory używają środowiska Winres. exe do edytowania etykiet kontrolek i dostosowywania lokalizacji i rozmiaru formantów w celu dostosowania ich do etykiet dla kultury docelowej.

Jeśli Winres.exe nie może rozpoznać typu formantu, utworzy formant zastępczy formantu w zlokalizowanym pliku resources lub resx. Symbol zastępczy formantu pojawia się w formularzu Windows Forms jako okno zakreskowane. Rozmiar i położenie zakreskowanego okna są zgodne z rzeczywistym formantem. Wszystkie dostępne lokalizowalne właściwości kontrolki symbolu zastępczego pojawiają się w oknie **Właściwości** . Wszelkie zmiany wprowadzone do symbolu zastępczego formantu są zapisywane dla rzeczywistego formantu.

## <a name="winresexe-versus-visual-studio"></a>Winres.exe a Visual Studio

Ogólnie rzecz biorąc, przed rozpoczęciem lokalizowania formularzy Windows Forms aplikacji należy zadecydować, czy jako narzędzia do lokalizacji używać programu Visual Studio czy Winres.exe. Zgodność wersji opisana poniżej może uniemożliwić przejście od jednego narzędzia do drugiego.

Zaletą programu Visual Studio jest to, że można za jego pomocą tworzyć i lokalizować aplikacje. Aby zlokalizować formularz, po zakończeniu opracowywania ustaw wartość <xref:System.ComponentModel.LocalizableAttribute> formularza ( **lokalizowalną** właściwość w edytorze **Właściwości** ) `true` i zmień jej właściwość **Language** na pożądaną kulturę docelową. Następnie należy przeprowadzić edycję ciągów i dostosować położenie i rozmiar formantów, aby pomieściły ciągi dla kultury docelowej. Podczas zapisywania zlokalizowanego pliku resx Visual Studio zapisuje w pliku tylko lokalizowalne właściwości (właściwości zmienione w docelowej kulturze). Program Visual Studio automatycznie tworzy zestaw satelicki dla zlokalizowanego pliku resx w lokalizacji odpowiedniego katalogu.

Chociaż program Visual Studio udostępnia zintegrowane środowisko deweloperskie i lokalizacyjne, program Winres. exe jest zalecanym narzędziem używanym w przypadku, gdy lokalizacja jest wykonywana przez lokalizatory innych firm. Ponieważ Winres.exe jest tylko narzędziem do lokalizacji, umożliwia jaśniejsze rozdzielenie kodu aplikacji od formularzy, które mają zostać zlokalizowane, co jest praktyczniejsze w przypadku zarządzania dużymi projektami.

## <a name="using-winresexe"></a>Korzystanie z Winres.exe

Aby zlokalizować przy użyciu programu Winres. exe, należy najpierw opracować aplikację przy użyciu projektanta wizualnego, takiego jak **Projektant formularzy systemu Windows** w programie Visual Studio. <xref:System.ComponentModel.LocalizableAttribute> Po zakończeniu opracowywania ustaw wartość w formularzu ( **lokalizowalna** właściwość w edytorze **Właściwości** ) `true`, a następnie przejdź do pliku resx dla domyślnej kultury do lokalizatora innej firmy. Ten plik resx zawiera dodatkowe informacje, których Winres.exe używa do odtworzenia wersji oryginalnego formularza z czasu projektowania.

> [!NOTE]
> Programu Winres.exe nie można używać do edytowania domyślnego pliku zasobów. Winres.exe interpretuje wszystkie zmienione właściwości jako właściwości zlokalizowane i zapisuje je do pliku zasobów docelowej kultury.

Ostateczna wersja pliku zasobów kultury może zostać użyta do utworzenia zlokalizowanej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach klasycznych](../resources/index.md).

Środowiska Winres. exe mają następujące funkcje i możliwości:

- Winres może działać w trybie pojedynczego pliku (SFM) lub w trybie pliku Visual Studio (VSFM). SFM jest starszym trybem, w którym w pliku zasobów są zapisywane pełne informacje o formularzu i jego zawartość. W trybie VSFM w pliku zasobów zapisywane są tylko zmiany dotyczące kultury.

- Okno raportowanie błędów, zadokowane w lewym dolnym rogu okna głównego.

- Klawisze skrótów można sprawdzić pod kątem duplikatów: w menu **Format** kliknij polecenie **Sprawdź klawisze skrótów** .

## <a name="version-compatibility"></a>Zgodność wersji

Należy użyć wersji środowiska Winres. exe wydanej z używanym .NET Framework. W poniższej tabeli wymieniono zgodne wersje:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2.0|2.0|
|Visual Studio 2008|3.0 i 3.5|3.0 i 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> Chociaż tryb VSFM ma tę zaletę, że jest zgodny z programem Visual Studio, ponieważ są w nim zapisywane tylko zmienione wartości, program Winres.exe wymaga, aby w tym samym katalogu znajdował się pierwotny plik zasobów. Na przykład Edycja `TestApp.de-DE.resources`, niemiecki plik zasobów w Niemczech, wymaga obecności domyślnego pliku zasobów, `TestApp.resx`i ewentualnie pliku zasobów neutralnych dla kultury, `TestApp.de.resources`.

## <a name="examples"></a>Przykłady

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Aby zlokalizować plik resx lub .resources skojarzony z formularzem

1. Wpisz `winres` w wierszu polecenia dewelopera, aby uruchomić Winres. exe.

2. Aby otworzyć domyślne zasoby formularza do zlokalizowania, kliknij polecenie **Otwórz** w menu **plik** i przejdź do pliku, aby go otworzyć.

     —lub—

     Określ plik do otwarcia w wierszu polecenia podczas uruchamiania programu Winres.exe.

     Następujące polecenie uruchamia środowiska Winres. exe i ładuje formularz skojarzony z programem `TestApp.resx` w projektancie formularzy.

    ```console
    winres TestApp.resx
    ```

     Następujące polecenie uruchamia środowiska Winres. exe i ładuje formularz skojarzony z programem `TestApp.resources` w projektancie formularzy.

    ```console
    winres TestApp.resources
    ```

    > [!NOTE]
    > Jeśli formularz, którego zasoby są edytowane, jest odziedziczonym formularzem, zarówno zestaw zawierający formularz, po którym został odziedziczony edytowany formularz, jak i zestaw zawierający dziedziczący formularz muszą być albo zarejestrowane w globalnej pamięci podręcznej zestawów (GAC) lub znajdować się w tym samym katalogu co plik WinRes.exe. Aby uzyskać więcej informacji na temat instalowania składników .NET Framework w pamięci GAC, zobacz [Global Assembly Cache](../app-domains/gac.md).

3. Wybierz kontrolki w formularzu i zmień ich <xref:System.Windows.Forms.Control.Text%2A> właściwości i inne, aby odzwierciedlały Lokalizowaną kulturę i jej język. Przenoszenie lub zmienianie rozmiaru formantów w celu dostosowania zlokalizowanego tekstu.

4. Aby zapisać zlokalizowaną wersję pliku resx lub Resources, kliknij ikonę **Zapisz** lub to samo polecenie w menu **plik** . Narzędzie wyświetli okno **Wybierz kulturę** .

5. Wybierz odpowiednią kulturę i tryb plików, a następnie kliknij przycisk **OK**.

   Narzędzie zapisuje plik przy użyciu konwencji nazewnictwa, która jest oczekiwana w czasie wykonywania dla zlokalizowanych plików zasobów. Na przykład w przypadku zlokalizowania `TestApp.resources` dla języka niemieckiego w Niemczech, narzędzie zapisuje plik jako. `TestApp.de-DE.resources` W przypadku zlokalizowania `TestApp.resx` dla języka niemieckiego w Niemczech narzędzie zapisuje plik jako. `TestApp.de-DE.resx` Aby uzyskać więcej informacji na temat konwencji nazewnictwa zasobów, zobacz [pakowanie i wdrażanie zasobów](../resources/packaging-and-deploying-resources-in-desktop-apps.md). Aby zapoznać się z listą wstępnie zdefiniowanych nazw kultur używanych w czasie wykonywania, zobacz <xref:System.Globalization.CultureInfo> Klasa.

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Narzędzia](index.md)
- [Zasoby w aplikacjach klasycznych](../resources/index.md)
- [Globalizacja i lokalizacja](../../standard/globalization-localization/index.md)
