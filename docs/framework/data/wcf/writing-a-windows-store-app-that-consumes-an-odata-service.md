---
title: "Pisanie aplikacji ze Sklepu Windows korzystającą z usługi OData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a2eb79e8bf8a5c683c9d48a0a69e4d7f5d270eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a>Pisanie aplikacji ze Sklepu Windows korzystającą z usługi OData
Został wprowadzony nowy typ aplikacji systemu Windows 8: aplikacji ze Sklepu Windows. Aplikacje ze Sklepu Windows nowy wygląd i sposób działania, uruchom na różnych urządzeniach i stają się dostępne w Sklepie Windows. W tym temacie opisano sposób zapisania korzystającą z usługi OData, w szczególności usługi OData katalogu NetFlix aplikacji ze Sklepu Windows. Aby uzyskać więcej informacji dotyczących aplikacji ze Sklepu Windows, przeczytaj [wprowadzenie do korzystania z aplikacji ze Sklepu Windows](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
1.  [System Microsoft Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [Microsoft Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [Usługi danych WCF](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a>Tworzenie domyślne siatki aplikację ze Sklepu Windows  
  
1.  Tworzenie aplikacji siatki nowego magazynu systemu Windows przy użyciu języka C# i języka XAML. Nazwa aplikacji OData.WindowsStore.NetflixDemo:  
  
     ![Okno dialogowe nowego projektu](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")  
  
2.  Otwórz Package.appxmanifest, a następnie wprowadź przyjazną nazwę w polu tekstowym Nazwa wyświetlana. Określa nazwę aplikacji używane z systemu Windows 8 funkcji wyszukiwania.  
  
     ![Plik manifestu aplikacji](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")  
  
3.  Wprowadź przyjazną nazwę w \<nazwa_aplikacji > w pliku App.xaml. To ustawienie jest wyświetlane, gdy aplikacja jest uruchamiana nazwy aplikacji:  
  
     ![Plik App.XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")  
  
4.  Skompiluj i uruchom aplikację. Najpierw Zobacz ekranu powitalnego aplikacji. Poniższy zrzut ekranu przedstawia domyślnego ekranu powitalnego. Obraz używany jest przechowywany w folderze Zasoby projektu.  
  
     ![Ekran powitalny aplikacji domyślne](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")  
  
     Następnie zostanie wyświetlony aplikacji.  
  
     ![Domyślna aplikacja](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")  
  
     Domyślna aplikacja definiuje zestaw klas w SampleDataSource.cs: SampleDataGroup i SampleDataItem, które są pochodnymi SampleDataCommon, które jest pochodną BindableBase. SampleDataGroup i SampleDataItem są powiązane z domyślnego widoku GridView. SampleDataSource.cs znajduje się w folderze DataModel w projekcie NetflixDemo. Aplikacja wyświetla zgrupowaną kolekcję. Każda grupa zawiera dowolną liczbę elementów reprezentowana odpowiednio przez SampleDataGroup, SampleDataItem, a. Poprzedni zrzut ekranu zawiera grupę o nazwie grupy 1 tytuł i wszystkie elementy w grupie wyświetlane razem.  
  
     Strona główna aplikacji jest GroupedItemsPage.xaml. Zawiera on element GridView wyświetlający przykładowe dane utworzone przez klasę SampleDataSource.cs. GroupedItemsPage jest ładowany przez App.xaml.cs w wywołaniu rootFrame.Navigate:  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     Powoduje to GroupedItemsPage z myślą o uruchamianiu i jego LoadState metoda jest wywoływana. LoadState powoduje, że statycznego wystąpienia klas SampleDataSource ma zostać utworzony, który tworzy kolekcję obiektów SampleDataGroup. Każdy obiekt SampleDataGroup zawiera kolekcję obiektów SampleDataItem. LoadState są przechowywane w kolekcji obiektów SampleDataGroup w DefaultViewModel:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     Metody DefaultViewModel następnie jest powiązany z widoku GridView. To jest przywoływany w pliku GroupedItemsPage.xaml podczas konfigurowania powiązania danych.  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     CollectionViewSource jest używany jako serwer proxy dla obsługi grupowanych kolekcji. W przypadku powiązania iterację kolekcji obiektów SampleDataGroup, aby wypełnić widoku GridView.  Atrybut ItemsPath informuje CollectionViewSource, jakie właściwości dla każdego obiektu SampleDataGroup, aby znaleźć SampleDataItems zawiera. W takim przypadku każdy obiekt SampleDataGroup zawiera kolekcję TopItems SampleDataItem obiektów.  
  
     Dla aplikacji Netflix filmy są pogrupowane według rodzaju. Dlatego aplikacji Wyświetla numer gatunkami muzyki i listy filmów w ramach tego rodzaju.  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a>Dodawanie odwołania do usługi do usługi Netflix OData  
  
1.  Zanim firma Microsoft może wprowadzać żadnych wywołań do usługi Netflix OData musimy dodać odwołanie do usługi. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz opcję Dodaj odwołanie do usługi...  
  
     ![Dodaj odwołanie do usługi w oknie dialogowym](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")  
  
2.  Wprowadź adres URL usługi Netflix OData na pasku adresu i kliknij Przejdź. Ustaw Namespace odwołania do usługi do Netflix, a następnie kliknij przycisk OK.  
  
     ![Dodaj błąd odwołania usługi](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")  
  
    > [!NOTE]
    >  Jeśli nie został jeszcze zainstalowany [WCF Data Services narzędzia dla aplikacji ze Sklepu Windows](http://go.microsoft.com/fwlink/p/?LinkId=266652), zostanie wyświetlony monit z następującym komunikatem, takie jak powyżej. Należy pobrać i zainstalować narzędzia, do którego odwołuje się łącze, aby kontynuować.  
  
 Dodanie odwołania do usługi generuje silnie typizowanej klasy korzystające usługi danych WCF można przeanalizować OData zwrócony przez usługę Netflix OData. Klas zdefiniowanych w SampleDataSource.cs może być powiązana z widoku GridView, więc musimy przenoszenie danych do powiązania klas zdefiniowanych w SampleDataSource.cs wygenerowane klasy klienta OData.  Aby to zrobić, należy wprowadzić kilka zmian w modelu danych zdefiniowanych w SampleDataSource.cs.  
  
#### <a name="update-the-data-model-for-the-application"></a>Aktualizacja modelu danych dla aplikacji  
  
1.  Zastąp istniejący kod w SampleDataSource.cs kod z [tego gist](https://gist.github.com/3419288). Zaktualizowany kod dodaje metodę LoadMovies (do klasy klas SampleDataSource), która wykonuje kwerendy względem usługi Netflix OData i wypełnia listę gatunkami muzyki (allGroups) i w obrębie każdego rodzaju listy filmów. Klasa SampleDataGroup jest używana do reprezentowania określonego rodzaju i klasa SampleDataItem jest używana do reprezentowania filmu.  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     [Wzorca asynchronicznego opartego na zadaniach](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) jest używany do asynchronicznie pobierania 300 (wykonaj) ostatnie (OrderByDescending) PG oceną (filmy kopię z Netflix gdzie). Pozostała część kod tworzy SimpleDataItems i SimpleDataGroups z jednostkami, które zostały zwrócone w źródle strumieniowym OData.  
  
     Klasa klas SampleDataSource implementuje również metody proste wyszukiwanie. W takim przypadku tak proste wyszukiwanie w pamięci filmów załadowany.  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     Również w SampleDataSource.cs klasy o nazwie ExtensionMethods jest zdefiniowany. Każda z tych metod rozszerzenia korzysta ze wzorca NACIŚNIJ umożliwia klas SampleDataSource, można wykonać zapytania OData bez blokowania interfejsu użytkownika. Na przykład następujący kod używa metody Task.Factory.FromAsync do zaimplementowania NACIŚNIJ.  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     Jak aplikacja domyślna strona główna aplikacji jest GroupedItemsPage. Teraz, jednak Wyświetla filmy pobierane z Netflix pogrupowane według rodzaju.  Podczas tworzenia wystąpienia klasy GroupedItemsPage jego LoadState — metoda jest wywoływana. LoadState powoduje, że statycznego wystąpienia klas SampleDataSource, należy utworzyć nawiązywania połączenia z usługą Netflix OData zgodnie z opisem wcześniej. LoadState przechowuje kolekcji gatunkami muzyki (SampleDataGroup obiekty) w DefaultViewModel:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     Jak opisano wcześniej, DefaultViewModel jest następnie używany do wiązania danych do widoku GridView.  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a>Dodaj umowy wyszukiwania umożliwiają aplikację do uczestnictwa w wyszukiwania systemu Windows  
  
1.  Dodaj umowy wyszukiwania w aplikacji. Umożliwia to aplikacji do integracji z wyników wyszukiwania systemu Windows 8. Nazwa kontraktu wyszukiwania SearchResultsPage.xaml  
  
     ![Dodaj umowy wyszukiwania](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")  
  
2.  Zmodyfikuj wiersza 58 SearchResultsPage.xaml.cs przez usunięcie osadzonych stawiać cudzysłów wokół queryText.  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  Wstaw następujące dwa wiersze kodu w wierszu 81 SearchResultsPage.xaml.cs można pobrać wyników wyszukiwania.  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 Gdy użytkownik wywołuje wyszukiwania systemu Windows, typów w terminu wyszukiwania i go dotyka pokaz Netflix ikonę aplikacji na pasku wyszukiwania, metodzie LoadState SearchResultsPage jest wykonywana. Parametr nawigacji wysyłane do LoadState zawiera tekst zapytania. Następnie metoda Filter_SelectionChanged jest wywoływana, które, a następnie wywołuje metodę wyszukiwania w klasie klas SampleDataSource. Wyniki są zwracane, a następnie wyświetlane na stronie SearchResultsPage.xaml.  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 Aby uzyskać więcej informacji na temat integracji wyszukiwania aplikacji, zobacz [wyszukiwania: integrowanie środowiska wyszukiwania systemu Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266650).  
  
## <a name="run-the-application"></a>Uruchamianie aplikacji  
 Uruchom aplikację, naciskając klawisz F5. Należy pamiętać, że potrwa kilka sekund do ładowania obrazów podczas uruchamiania aplikacji. Ponadto pierwsza próba wyszukiwania nie może zwracać żadnych wyników. W przypadku aplikacji rzeczywistych należy uwzględniać oba te problemy.  
  
 Aplikacja wywołuje usługę Netflix OData, odbiera dane w wygenerowane klasy klienta OData, a następnie przesyła dane do klasy powiązania danych (klas SampleDataSource, SampleDataGroup i SampleDataItem). Aby powiązać dane z widoku GridView używa tych klas może być powiązana. Jeśli użytkownik nie zna działania można znaleźć XAML databinding [jak grupować elementy na liście lub siatki (aplikacje ze Sklepu Windows przy użyciu języka C# / VB/C++ i XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).
