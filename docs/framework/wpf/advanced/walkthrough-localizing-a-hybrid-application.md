---
title: "Wskazówki: lokalizacja aplikacji hybrydowej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f9bb7588ef1f6962a5cd55196154ac7f666d53b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Wskazówki: lokalizacja aplikacji hybrydowej
W tym przewodniku przedstawiono sposób localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-hybrydowych aplikacji.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu hosta.  
  
-   Dodawanie zawartości lokalizowalny.  
  
-   Włączanie lokalizacji.  
  
-   Przypisywanie identyfikatorów zasobów.  
  
-   Tworzy zestaw satelicki przy użyciu narzędzia LocBaml  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [lokalizowanie przykładowej aplikacji hybrydowych](http://go.microsoft.com/fwlink/?LinkID=160015).  
  
 Gdy skończysz, masz aplikację zlokalizowanych hybrydowego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-windows-forms-host-project"></a>Tworzenie projektu hosta formularzy systemu Windows  
 Pierwszym krokiem jest utworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji projektu i dodać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element z zawartością, która będzie localize.  
  
#### <a name="to-create-the-host-project"></a>Aby utworzyć projekt z hosta  
  
1.  Utwórz projekt aplikacji WPF o nazwie `LocalizingWpfInWf`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dodaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> element o nazwie `SimpleControl` do projektu.  
  
3.  Użyj <xref:System.Windows.Forms.Integration.ElementHost> formantu, aby umieścić `SimpleControl` elementu na formularzu. Aby uzyskać więcej informacji, zobacz [wskazówki: 3-formantu złożonego WPF w formularzach systemu Windows obsługującego](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).  
  
## <a name="adding-localizable-content"></a>Dodawanie zlokalizowania zawartości  
 Następnie należy dodać [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] etykiety formantu i ustawić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości elementu do zlokalizowania ciągu.  
  
#### <a name="to-add-localizable-content"></a>Aby dodać zlokalizowania zawartości  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie **SimpleControl.xaml** aby otworzyć go w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  Ustaw zawartość <xref:System.Windows.Controls.Button> kontrolować, używając następującego kodu.  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  W Eksploratorze rozwiązań kliknij dwukrotnie **Form1** aby otworzyć go w narzędziu Projektant dla formularzy systemu Windows.  
  
4.  Otwórz przybornika i kliknij dwukrotnie **etykiety** można dodać formantu etykiety do formularza. Ustaw wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwości `"Hello"`.  
  
5.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     Zarówno `SimpleControl` elementu i formantu etykiety wyświetlić tekst **"Hello"**.  
  
## <a name="enabling-localization"></a>Włączanie lokalizacji  
 Projektant formularzy systemu Windows zawiera ustawienia dotyczące włączania lokalizacji w zestawie satelickim.  
  
#### <a name="to-enable-localization"></a>Aby włączyć lokalizacji  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie **pliku Form1.cs** aby otworzyć go w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  W oknie właściwości ustaw wartość w formie **Localizable** właściwości `true`.  
  
3.  W oknie właściwości ustaw wartość **języka** właściwości **hiszpański (Hiszpania)**.  
  
4.  W narzędziu Projektant dla formularzy systemu Windows wybierz formantu etykiety.  
  
5.  W oknie właściwości ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości `"Hola"`.  
  
     Plik zasobów o nazwie Form1.es ES.resx jest dodane do projektu.  
  
6.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliku Form1.cs** i kliknij przycisk **kod widoku** aby otworzyć go w edytorze kodu.  
  
7.  Skopiuj następujący kod do `Form1` Konstruktor poprzedzających wywołanie `InitializeComponent`.  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **LocalizingWpfInWf** i kliknij przycisk **Zwolnij projekt**.  
  
     Nazwa projektu jest oznaczony **(niedostępne)**.  
  
9. Kliknij prawym przyciskiem myszy **LocalizingWpfInWf**i kliknij przycisk **Edytuj LocalizingWpfInWf.csproj**.  
  
     Plik projektu zostanie otwarty w edytorze kodu.  
  
10. Skopiuj następujący wiersz do pierwszego `PropertyGroup` w pliku projektu.  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. Zapisz plik projektu i zamknij go.  
  
12. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **LocalizingWpfInWf** i kliknij przycisk **Załaduj ponownie projekt**.  
  
## <a name="assigning-resource-identifiers"></a>Przypisywanie identyfikatory zasobów  
 Zlokalizowania zawartości można mapować na zestawy zasobów, przy użyciu identyfikatorów zasobów. Po określeniu aplikacji MsBuild.exe automatycznie przypisuje identyfikatory zasobów `updateuid` opcji.  
  
#### <a name="to-assign-resource-identifiers"></a>Aby przypisać identyfikatory zasobów  
  
1.  Z Start Menu, otwórz [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] wiersza polecenia.  
  
2.  Użyj następującego polecenia, aby przypisać identyfikatory zasobów do zlokalizowania zawartości.  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  W Eksploratorze rozwiązań kliknij dwukrotnie **SimpleControl.xaml** aby otworzyć go w edytorze kodu. Zostanie wyświetlone `msbuild` polecenia został dodany `Uid` atrybutu do wszystkich elementów. Ułatwia to lokalizacja poprzez przypisywanie identyfikatorów zasobów.  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  Naciśnij klawisz F6 w celu skompilowania rozwiązania.  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Przy użyciu LocBaml w celu utworzenia zestawu satelickiego  
 Zlokalizowane zawartość jest przechowywana w tylko do zasobów *zestawu satelickiego*. Użyj narzędzia wiersza polecenia LocBaml.exe wygenerowało zlokalizowanych zestawu dla Twojego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  
  
#### <a name="to-produce-a-satellite-assembly"></a>Aby utworzyć zestaw satelicki  
  
1.  Skopiuj LocBaml.exe do folderu obj\Debug Twojego projektu. Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).  
  
2.  W oknie wiersza polecenia użyj następującego polecenia, aby wyodrębnić ciągów zasobów do pliku tymczasowego.  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  Otwórz plik temp.csv z [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] lub innego edytora tekstu. Zastąp ciąg `"Hello"` z jego hiszpańskim tłumaczenia `"Hola"`.  
  
4.  Zapisz plik temp.csv.  
  
5.  Użyj następującego polecenia, aby wygenerować plik zlokalizowanych zasobów.  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     Plik LocalizingWpfInWf.g.es ES.resources jest tworzony w folderze obj\Debug.  
  
6.  Użyj następującego polecenia do kompilacji zestawu satelickiego zlokalizowane.  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     Plik LocalizingWpfInWf.resources.dll jest tworzony w folderze obj\Debug.  
  
7.  Skopiuj plik LocalizingWpfInWf.resources.dll do folderu bin\Debug\es ES projektu. Zastąp istniejący plik.  
  
8.  Uruchom LocalizingWpfInWf.exe, który znajduje się w folderze bin\Debug Twojego projektu. Nie odbudować aplikacji lub zestawu satelickiego zostaną zastąpione.  
  
     Aplikacja zawiera zlokalizowane ciągi zamiast ciągów angielskiej wersji językowej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [Wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
