---
title: "Winres.exe (Edytor zasobów formularzy systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8009f832434d6bbad2ad7bee9cbfd62c81d623c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="winresexe-windows-forms-resource-editor"></a>Winres.exe (Edytor zasobów formularzy systemu Windows)
Edytor zasobów Windows Forms, Winres.exe, jest narzędziem układu wizualnego, które ułatwia ekspertom lokalizowanie zasobów interfejsu użytkownika Windows Forms używanych przez formularze. Pliki resx lub resources używane jako dane wejściowe do Winres.exe mogą być tworzone przy użyciu środowiska projektowania wizualnego, takiego jak Microsoft Visual Studio. Aby uzyskać informacje na temat wdrażania zasobów w aplikacjach .NET Framework, zobacz [zasobów w aplikacjach pulpitu](../../../docs/framework/resources/index.md).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
winres resourceFile   
winres /?   
```  
  
## <a name="remarks"></a>Uwagi  
  
|Argument|Opis|  
|--------------|-----------------|  
|`resourceFile`|Plik zasobów do zlokalizowania. Ten plik musi być plikiem resx lub resources formularza Windows Forms wygenerowanym przez projektanta programu Visual Studio. Winres.exe nie może otwierać rodzajowych plików resx i resources.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
 Stan elementów interfejsu użytkownika z formularza w projekcie programu Windows Forms jest zazwyczaj zapisywany w plikach zasobów, które są albo plikami XML z rozszerzeniem resx, lub odpowiednio skompilowanymi wersjami binarnymi z rozszerzeniem resources. Winres.exe jest narzędziem, które umożliwia ograniczone edytowanie obu typów plików poza środowiskiem projektowania programu Visual Studio. W szczególności umożliwia następujące rodzaje operacji edycji:  
  
-   Plik zasobów kultury neutralnej lub określonej można edytować, aby zmienić właściwości interfejsu użytkownika formularza lub jego formantów, takich jak ich tekst, rozmiar lub położenie.  
  
-   Pliki zasobów kultury neutralnej lub określonej mogą być generowane z domyślnego pliku zasobów.  
  
-   Plik zasobów kultury można zapisać jako inny plik zasobów kultury. Na przykład plik zasobów Angielski (USA) można zapisać jako plik zasobów Polski. Zazwyczaj nowy plik będzie można później edytować, aby był zgodny z nową kulturą.  
  
 Zobacz też [hierarchiczna organizacja zasobów do lokalizacji](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\)) lub [hierarchiczna organizacja zasobów do lokalizacji](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\)).  
  
 Winres.exe nie może skonwertować pliku resx na odpowiedni plik resources; użyj narzędzia Resgen.exe. Aby uzyskać więcej informacji o Resgen.exe, zobacz [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 Winres.exe jest aplikacją graficzną, która odtwarza wersję formularza Windows Forms czasu projektowania z samego pliku zasobów, bez dostępu do kodu źródłowego. Winres.exe obsługuje okno projektanta formularzy Windows Forms i właściwości programu Visual Studio. Te funkcje umożliwiają wizualne edytowanie pliku resources lub resx zawierającego formularz Windows Forms. Zazwyczaj lokalizatorzy używają aplikacji Winres.exe do edytowania etykiet formantów w celu dostosowania położenia i rozmiaru formantów, aby pomieściły etykiety docelowej kultury.  
  
 Jeśli Winres.exe nie może rozpoznać typu formantu, utworzy formant zastępczy formantu w zlokalizowanym pliku resources lub resx. Symbol zastępczy formantu pojawia się w formularzu Windows Forms jako okno zakreskowane. Rozmiar i położenie zakreskowanego okna są zgodne z rzeczywistym formantem. Wszystkie dostępne lokalizowalne właściwości symbolu zastępczego formantu są wyświetlane w oknie dialogowym Właściwości. Wszelkie zmiany wprowadzone do symbolu zastępczego formantu są zapisywane dla rzeczywistego formantu.  
  
## <a name="winresexe-versus-visual-studio"></a>Winres.exe a Visual Studio  
 Ogólnie rzecz biorąc, przed rozpoczęciem lokalizowania formularzy Windows Forms aplikacji należy zadecydować, czy jako narzędzia do lokalizacji używać programu Visual Studio czy Winres.exe. Zgodność wersji opisana poniżej może uniemożliwić przejście od jednego narzędzia do drugiego.  
  
 Zaletą programu Visual Studio jest to, że można za jego pomocą tworzyć i lokalizować aplikacje. Do zlokalizowania formularz, po zakończeniu tworzenia, ustaw formularza <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** właściwość w edytorze właściwości) do `true` i zmień jego **języka** właściwości Żądana kulturze docelowej. Następnie należy przeprowadzić edycję ciągów i dostosować położenie i rozmiar formantów, aby pomieściły ciągi dla kultury docelowej. Podczas zapisywania zlokalizowanego pliku resx Visual Studio zapisuje w pliku tylko lokalizowalne właściwości (właściwości zmienione w docelowej kulturze). Program Visual Studio automatycznie tworzy zestaw satelicki dla zlokalizowanego pliku resx w lokalizacji odpowiedniego katalogu.  Zobacz też [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\)).  
  
 Wprawdzie Visual Studio stanowi zintegrowane środowisko deweloperskie i lokalizacyjne, ale zaleca się używanie aplikacji Winres.exe, jeśli lokalizacja będzie wykonywana przez zewnętrznych lokaliztorów. Ponieważ Winres.exe jest tylko narzędziem do lokalizacji, umożliwia jaśniejsze rozdzielenie kodu aplikacji od formularzy, które mają zostać zlokalizowane, co jest praktyczniejsze w przypadku zarządzania dużymi projektami.  
  
## <a name="using-winresexe"></a>Korzystanie z Winres.exe  
 W przypadku lokalizowania za pomocą Winres.exe najpierw musisz opracować aplikację przy użyciu projektanta graficznego, takiego jak Projektant formularzy czy Visual Studio. Po zakończeniu tworzenia ustawić formularza <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** właściwość w edytorze właściwości) do `true`, a następnie przekazują plik .resx dla kultury domyślnej do lokalizatora innych firm. Ten plik resx zawiera dodatkowe informacje, których Winres.exe używa do odtworzenia wersji oryginalnego formularza z czasu projektowania.  
  
> [!CAUTION]
>  Programu Winres.exe nie można używać do edytowania domyślnego pliku zasobów. Winres.exe interpretuje wszystkie zmienione właściwości jako właściwości zlokalizowane i zapisuje je do pliku zasobów docelowej kultury.  
  
 Ostateczna wersja pliku zasobów kultury może zostać użyta do utworzenia zlokalizowanej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [zasobów w aplikacjach pulpitu](../../../docs/framework/resources/index.md).  
  
 Winres.exe w wersji 2.0 ma następujące funkcje i możliwości:  
  
-   Winres może działać w trybie pojedynczego pliku (SFM) lub w trybie pliku Visual Studio (VSFM). SFM jest starszym trybem, w którym w pliku zasobów są zapisywane pełne informacje o formularzu i jego zawartość. W trybie VSFM w pliku zasobów zapisywane są tylko zmiany dotyczące kultury.  
  
-   Do interfejsu programu zostało dodane okno raportowania błędów zadokowane w lewym dolnym rogu okna głównego.  
  
-   Klawisze dostępu mogą być sprawdzane pod kątem duplikatów: w Format menu kliknij **Sprawdź klawisze dostępu** polecenia.  
  
## <a name="version-compatibility"></a>Zgodność wersji  
 Ponieważ w czasie między wydaniem programów Visual Studio .NET 2002 i Visual Studio 2005 zmienił się format plików zasobów, konieczne było wprowadzenie stosownych zmian w programie Winres.exe. Dlatego należy się kierować następującą ogólną zasadą: używać wersji Winres.exe wydanej z platformą .NET Framework używaną do tworzenia aplikacji. W tabeli poniżej wymieniono zgodne wersje.  
  
|Visual Studio|.NET Framework|Winres.exe|  
|-------------------|--------------------|----------------|  
|Visual Studio .NET 2002|1.0|1.0|  
|Visual Studio .NET 2003|1.1|1.1|  
|Visual Studio 2005|2.0|2.0|  
|Visual Studio 2008|3.0 i 3.5|3.0 i 3.5|  
|Visual Studio 2010|4.0|4.0|  
  
 Jeśli spróbujesz otworzyć starszy plik zasobów za pomocą wersji 2.0 programu Winres.exe, pojawi się monit o uaktualnienie formatu pliku do zgodnego z wersją 2.0 platformy .NET Framework.  
  
 W wersjach programu. NET Framework wcześniejszych niż 2.0 programy Winres.exe i Projektant formularzy programu Visual Studio tworzyły niezgodne pliki zasobów neutralne pod względem kultury i specyficzne dla kultury. Dlatego, gdy proces lokalizacji już się rozpoczął, trzeba było nadal używać tego samego narzędzia. Jednak z wersji 2.0 programu Winres.exe dodano tryb pliku Visual Studio (VSFM). Jak nazwa wskazuje, można edytować plik zasobów zapisany w tym trybie zgodności w dowolnym z tych narzędzi.  
  
> [!NOTE]
>  Chociaż tryb VSFM ma tę zaletę, że jest zgodny z programem Visual Studio, ponieważ są w nim zapisywane tylko zmienione wartości, program Winres.exe wymaga, aby w tym samym katalogu znajdował się pierwotny plik zasobów. Na przykład edytowanie `TestApp.de-DE.resources`, niemiecki w pliku zasobu w Niemczech wymaga obecności domyślnego pliku zasobów `TestApp.resx`i prawdopodobnie pliku zasobu niezależny od kultury, `TestApp.de.resources`.  
  
## <a name="examples"></a>Przykłady  
  
#### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Aby zlokalizować plik resx lub .resources skojarzony z formularzem  
  
1.  Typ `winres` developer wiersza polecenia do uruchomienia Winres.exe.  
  
2.  Aby otworzyć domyślnych zasobów dla formularza do zlokalizowania, kliknij przycisk **Otwórz** na **pliku** menu i przejdź do pliku, aby go otworzyć.  
  
     —lub—  
  
     Określ plik do otwarcia w wierszu polecenia podczas uruchamiania programu Winres.exe.  
  
     Polecenie uruchamia Winres.exe i załaduje formularz skojarzony z `TestApp.resx` w Projektancie formularza.  
  
    ```  
    winres TestApp.resx  
    ```  
  
     Polecenie uruchamia Winres.exe i załaduje formularz skojarzony z `TestApp.resources` w Projektancie formularza.  
  
    ```  
    winres TestApp.resources  
    ```  
  
    > [!NOTE]
    >  Jeśli formularz, którego zasoby są edytowane, jest odziedziczonym formularzem, zarówno zestaw zawierający formularz, po którym został odziedziczony edytowany formularz, jak i zestaw zawierający dziedziczący formularz muszą być albo zarejestrowane w globalnej pamięci podręcznej zestawów (GAC) lub znajdować się w tym samym katalogu co plik WinRes.exe. Aby uzyskać więcej informacji o instalowaniu składników .NET Framework w pamięci podręcznej GAC, zobacz [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).  
  
3.  Wybierz kontrolek w formularzu i zmień ich <xref:System.Windows.Forms.Control.Text%2A> i innych właściwości w celu uwzględnienia zlokalizowanych kultury i języka. Przenoszenie lub zmienianie rozmiaru formantów w celu dostosowania zlokalizowanego tekstu.  
  
4.  Aby zapisać zlokalizowanej wersji pliku .resx lub .resources, kliknij przycisk **zapisać** ikony lub tego samego polecenia na **pliku** menu. Narzędzie wyświetla **wybierz kultury** okna.  
  
5.  Wybierz odpowiedni tryb kultury i plików, a następnie kliknij przycisk **OK**. Narzędzie zapisuje plik przy użyciu konwencji nazewnictwa oczekiwanej w czasie wykonywania dla zlokalizowanych plików zasobów. Na przykład, jeśli użytkownik localize `TestApp.resources` na język niemiecki w Niemczech, narzędzie zapisuje plik jako `TestApp.de-DE.resources`. Jeśli użytkownik localize `TestApp.resx` na język niemiecki w Niemczech, narzędzie zapisuje plik jako `TestApp.de-DE.resx`. Aby uzyskać więcej informacji na temat konwencji nazewnictwa zasobów, zobacz [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać listę nazwy kultury wstępnie zdefiniowanych używane w czasie wykonywania, zobacz <xref:System.Globalization.CultureInfo> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.LocalizableAttribute>  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Resources.ResourceManager>  
 <xref:System.Resources.ResourceReader>  
 <xref:System.Resources.ResourceWriter>  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
 [Lokalizacja i globalizacja](../../../docs/standard/globalization-localization/index.md)
