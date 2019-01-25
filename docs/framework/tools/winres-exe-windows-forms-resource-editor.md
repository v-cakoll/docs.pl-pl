---
title: Winres.exe (Edytor lokalizacji zasobów Windows)
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
ms.openlocfilehash: 6732eef46f87d9e2e3aeada138ea28853d3f0479
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663169"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres.exe (Edytor lokalizacji zasobów Windows)

Edytor lokalizacji zasobów Windows, Winres.exe, jest narzędziem układu wizualnego, które ułatwia ekspertom lokalizowanie zasoby interfejsu użytkownika Windows Forms używanych przez formularze. Pliki resx lub resources używane jako dane wejściowe do Winres.exe mogą być tworzone przy użyciu środowiska projektowania wizualnego, takiego jak Microsoft Visual Studio. Aby uzyskać informacje na temat wdrażania zasobów w aplikacjach .NET Framework, zobacz [zasoby w aplikacjach pulpitu](../../../docs/framework/resources/index.md).

Winres.exe jest instalowany z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

## <a name="syntax"></a>Składnia

```
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

Zobacz też [hierarchiczna organizacja zasobów do lokalizacji](https://msdn.microsoft.com/library/756hydy4\(v=vs.110\)) lub [hierarchiczna organizacja zasobów do lokalizacji](https://msdn.microsoft.com/library/756hydy4\(v=vs.120\)).

Winres.exe nie może skonwertować pliku resx na odpowiedni plik resources; użyj narzędzia Resgen.exe. Aby uzyskać więcej informacji na temat Resgen.exe, zobacz [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

Winres.exe jest aplikacją graficzną, która odtwarza wersję formularza Windows Forms czasu projektowania z samego pliku zasobów, bez dostępu do kodu źródłowego. Winres.exe obsługuje Visual Studio **projektanta formularzy systemu Windows Forms** i **właściwości** okna. Te funkcje umożliwiają wizualne edytowanie pliku resources lub resx zawierającego formularz Windows Forms. Zazwyczaj lokalizatorzy używają aplikacji Winres.exe do edytowania etykiet formantów i dostosować położenie i rozmiar formantów, aby pomieściły etykiety docelowej kultury.

Jeśli Winres.exe nie może rozpoznać typu formantu, utworzy formant zastępczy formantu w zlokalizowanym pliku resources lub resx. Symbol zastępczy formantu pojawia się w formularzu Windows Forms jako okno zakreskowane. Rozmiar i położenie zakreskowanego okna są zgodne z rzeczywistym formantem. Wszystkie dostępne lokalizowalne właściwości symbolu zastępczego formantu są wyświetlane w **właściwości** okna. Wszelkie zmiany wprowadzone do symbolu zastępczego formantu są zapisywane dla rzeczywistego formantu.

## <a name="winresexe-versus-visual-studio"></a>Winres.exe a Visual Studio

Ogólnie rzecz biorąc, przed rozpoczęciem lokalizowania formularzy Windows Forms aplikacji należy zadecydować, czy jako narzędzia do lokalizacji używać programu Visual Studio czy Winres.exe. Zgodność wersji opisana poniżej może uniemożliwić przejście od jednego narzędzia do drugiego.

Zaletą programu Visual Studio jest to, że można za jego pomocą tworzyć i lokalizować aplikacje. Aby zlokalizować formularz, po zakończeniu tworzenia, ustaw dla formularza <xref:System.ComponentModel.LocalizableAttribute> ( **Lokalizowalny** właściwość **właściwości** edytora) do `true` i zmień jego  **Język** właściwości kultury wybraną docelową. Następnie należy przeprowadzić edycję ciągów i dostosować położenie i rozmiar formantów, aby pomieściły ciągi dla kultury docelowej. Podczas zapisywania zlokalizowanego pliku resx Visual Studio zapisuje w pliku tylko lokalizowalne właściwości (właściwości zmienione w docelowej kulturze). Program Visual Studio automatycznie tworzy zestaw satelicki dla zlokalizowanego pliku resx w lokalizacji odpowiedniego katalogu.

Mimo że program Visual Studio udostępnia zintegrowane środowisko deweloperskie i lokalizacyjne, Winres.exe jest zalecanym narzędziem do użycia, jeśli lokalizacja jest wykonywane przez zewnętrznych lokaliztorów. Ponieważ Winres.exe jest tylko narzędziem do lokalizacji, umożliwia jaśniejsze rozdzielenie kodu aplikacji od formularzy, które mają zostać zlokalizowane, co jest praktyczniejsze w przypadku zarządzania dużymi projektami.

## <a name="using-winresexe"></a>Korzystanie z Winres.exe

Lokalizowania za pomocą Winres.exe, najpierw musisz opracować aplikację przy użyciu wizualnego projektanta polubienie **Windows Forms Designer** w programie Visual Studio. Po zakończeniu tworzenia, ustaw dla formularza <xref:System.ComponentModel.LocalizableAttribute> ( **Lokalizowalny** właściwość **właściwości** edytora) do `true`, a następnie przekazać plik Resx domyślnej kultury do zewnętrznemu lokalizatorowi. Ten plik resx zawiera dodatkowe informacje, których Winres.exe używa do odtworzenia wersji oryginalnego formularza z czasu projektowania.

> [!NOTE]
> Programu Winres.exe nie można używać do edytowania domyślnego pliku zasobów. Winres.exe interpretuje wszystkie zmienione właściwości jako właściwości zlokalizowane i zapisuje je do pliku zasobów docelowej kultury.

Ostateczna wersja pliku zasobów kultury może zostać użyta do utworzenia zlokalizowanej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach pulpitu](../../../docs/framework/resources/index.md).

Winres.exe ma następujące funkcje i możliwości:

- Winres może działać w trybie pojedynczego pliku (SFM) lub w trybie pliku Visual Studio (VSFM). SFM jest starszym trybem, w którym w pliku zasobów są zapisywane pełne informacje o formularzu i jego zawartość. W trybie VSFM w pliku zasobów zapisywane są tylko zmiany dotyczące kultury.

- Okno z raportowania błędów jest zadokowany do lewej dolnej części okna głównego.

- Można sprawdzić duplikaty: od **Format** menu, kliknij przycisk **Sprawdź klawisze skrótów** polecenia.

## <a name="version-compatibility"></a>Zgodność wersji

Należy użyć wersji winres.exe wydanej z .NET Framework, którego używasz. W poniższej tabeli wymieniono zgodne wersje:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2.0|2.0|
|Visual Studio 2008|3.0 i 3.5|3.0 i 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> Chociaż tryb VSFM ma tę zaletę, że jest zgodny z programem Visual Studio, ponieważ są w nim zapisywane tylko zmienione wartości, program Winres.exe wymaga, aby w tym samym katalogu znajdował się pierwotny plik zasobów. Na przykład Edycja `TestApp.de-DE.resources`, niemieckiego pliku zasobów w Niemczech, wymaga obecności domyślnego pliku zasobów `TestApp.resx`i ewentualnie pliku zasobów kultury neutralnej `TestApp.de.resources`.

## <a name="examples"></a>Przykłady

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Aby zlokalizować plik resx lub .resources skojarzony z formularzem

1.  Typ `winres` w wierszu polecenia dla deweloperów, aby uruchomić Winres.exe.

2.  Aby otworzyć domyślnych zasobów do formularza do zlokalizowania, kliknij przycisk **Otwórz** polecenie **pliku** menu i przejdź do pliku, aby go otworzyć.

     —lub—

     Określ plik do otwarcia w wierszu polecenia podczas uruchamiania programu Winres.exe.

     Następujące polecenie uruchamia program Winres.exe i ładuje formularz skojarzony z `TestApp.resx` w Projektancie formularza.

    ```
    winres TestApp.resx
    ```

     Następujące polecenie uruchamia program Winres.exe i ładuje formularz skojarzony z `TestApp.resources` w Projektancie formularza.

    ```
    winres TestApp.resources
    ```

    > [!NOTE]
    > Jeśli formularz, którego zasoby są edytowane, jest odziedziczonym formularzem, zarówno zestaw zawierający formularz, po którym został odziedziczony edytowany formularz, jak i zestaw zawierający dziedziczący formularz muszą być albo zarejestrowane w globalnej pamięci podręcznej zestawów (GAC) lub znajdować się w tym samym katalogu co plik WinRes.exe. Aby uzyskać więcej informacji na temat instalowania składników .NET Framework w GAC, zobacz [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).

3.  Zaznacz formanty formularza i zmień ich <xref:System.Windows.Forms.Control.Text%2A> i innych właściwości w celu odzwierciedlenia zlokalizowanej kultury i jej języka. Przenoszenie lub zmienianie rozmiaru formantów w celu dostosowania zlokalizowanego tekstu.

4.  Aby zapisać zlokalizowaną wersję pliku ResX lub Resources, kliknij przycisk **Zapisz** ikony lub tego samego polecenia na **pliku** menu. Narzędzie wyświetli **Wybieranie kultury** okna.

5.  Wybierz odpowiednią kulturę i tryb pliku, a następnie kliknij przycisk **OK**.

   Narzędzie zapisuje plik przy użyciu konwencji nazewnictwa, która w czasie wykonywania dla zlokalizowanych plików zasobów. Na przykład, jeśli jest lokalizowany `TestApp.resources` dla języka niemieckiego w Niemczech, narzędzie zapisuje plik jako `TestApp.de-DE.resources`. Jeśli jest lokalizowany `TestApp.resx` dla języka niemieckiego w Niemczech, narzędzie zapisuje plik jako `TestApp.de-DE.resx`. Aby uzyskać więcej informacji dotyczących konwencji nazywania zasobów, zobacz [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać listę nazw wstępnie zdefiniowanych kultur używanych w czasie wykonywania, zobacz <xref:System.Globalization.CultureInfo> klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
