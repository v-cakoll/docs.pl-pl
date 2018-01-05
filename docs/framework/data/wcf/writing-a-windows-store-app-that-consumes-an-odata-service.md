---
title: "Pisanie aplikacji ze Sklepu Windows korzystającą z usługi OData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a2eb79e8bf8a5c683c9d48a0a69e4d7f5d270eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a><span data-ttu-id="30340-102">Pisanie aplikacji ze Sklepu Windows korzystającą z usługi OData</span><span class="sxs-lookup"><span data-stu-id="30340-102">Writing a Windows Store App that consumes an OData Service</span></span>
<span data-ttu-id="30340-103">Został wprowadzony nowy typ aplikacji systemu Windows 8: aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="30340-103">Windows 8 introduces a new type of application: the Windows Store app.</span></span> <span data-ttu-id="30340-104">Aplikacje ze Sklepu Windows nowy wygląd i sposób działania, uruchom na różnych urządzeniach i stają się dostępne w Sklepie Windows.</span><span class="sxs-lookup"><span data-stu-id="30340-104">Windows Store apps have a brand new look and feel, run on a variety of devices, and are made available on the Windows Store.</span></span> <span data-ttu-id="30340-105">W tym temacie opisano sposób zapisania korzystającą z usługi OData, w szczególności usługi OData katalogu NetFlix aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="30340-105">This topic describes how to write a Windows Store app that consumes an OData service, specifically the NetFlix Catalog OData service.</span></span> <span data-ttu-id="30340-106">Aby uzyskać więcej informacji dotyczących aplikacji ze Sklepu Windows, przeczytaj [wprowadzenie do korzystania z aplikacji ze Sklepu Windows](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span><span class="sxs-lookup"><span data-stu-id="30340-106">For more information about Windows Store Apps, please read [Getting Started with Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="30340-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="30340-107">Prerequisites</span></span>  
  
1.  [<span data-ttu-id="30340-108">System Microsoft Windows 8</span><span class="sxs-lookup"><span data-stu-id="30340-108">Microsoft Windows 8</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [<span data-ttu-id="30340-109">Microsoft Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="30340-109">Microsoft Visual Studio 2012</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [<span data-ttu-id="30340-110">Usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="30340-110">WCF Data Services</span></span>](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a><span data-ttu-id="30340-111">Tworzenie domyślne siatki aplikację ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="30340-111">Creating the default Windows Store Grid Application</span></span>  
  
1.  <span data-ttu-id="30340-112">Tworzenie aplikacji siatki nowego magazynu systemu Windows przy użyciu języka C# i języka XAML.</span><span class="sxs-lookup"><span data-stu-id="30340-112">Create a new Windows Store Grid Application using C# and XAML.</span></span> <span data-ttu-id="30340-113">Nazwa aplikacji OData.WindowsStore.NetflixDemo:</span><span class="sxs-lookup"><span data-stu-id="30340-113">Name the application OData.WindowsStore.NetflixDemo:</span></span>  
  
     <span data-ttu-id="30340-114">![Okno dialogowe nowego projektu](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span><span class="sxs-lookup"><span data-stu-id="30340-114">![New Project Dialog](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span></span>  
  
2.  <span data-ttu-id="30340-115">Otwórz Package.appxmanifest, a następnie wprowadź przyjazną nazwę w polu tekstowym Nazwa wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="30340-115">Open the Package.appxmanifest and enter a friendly name in the Display name text box.</span></span> <span data-ttu-id="30340-116">Określa nazwę aplikacji używane z systemu Windows 8 funkcji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="30340-116">This specifies the application name used with the Windows 8 search functionality.</span></span>  
  
     <span data-ttu-id="30340-117">![Plik manifestu aplikacji](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span><span class="sxs-lookup"><span data-stu-id="30340-117">![Application manifest file](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span></span>  
  
3.  <span data-ttu-id="30340-118">Wprowadź przyjazną nazwę w \<nazwa_aplikacji > w pliku App.xaml.</span><span class="sxs-lookup"><span data-stu-id="30340-118">Enter a friendly name in the \<AppName> element in the App.xaml file.</span></span> <span data-ttu-id="30340-119">To ustawienie jest wyświetlane, gdy aplikacja jest uruchamiana nazwy aplikacji:</span><span class="sxs-lookup"><span data-stu-id="30340-119">This sets the application name that is displayed when the application is launched:</span></span>  
  
     <span data-ttu-id="30340-120">![Plik App.XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span><span class="sxs-lookup"><span data-stu-id="30340-120">![App.xaml file](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span></span>  
  
4.  <span data-ttu-id="30340-121">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="30340-121">Build and launch the application.</span></span> <span data-ttu-id="30340-122">Najpierw Zobacz ekranu powitalnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30340-122">You first see the application’s splash screen.</span></span> <span data-ttu-id="30340-123">Poniższy zrzut ekranu przedstawia domyślnego ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="30340-123">The screenshot below displays the default splash screen.</span></span> <span data-ttu-id="30340-124">Obraz używany jest przechowywany w folderze Zasoby projektu.</span><span class="sxs-lookup"><span data-stu-id="30340-124">The image used is stored in the project’s Assets folder.</span></span>  
  
     <span data-ttu-id="30340-125">![Ekran powitalny aplikacji domyślne](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span><span class="sxs-lookup"><span data-stu-id="30340-125">![The default app splash screen](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span></span>  
  
     <span data-ttu-id="30340-126">Następnie zostanie wyświetlony aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30340-126">Then the application will be displayed.</span></span>  
  
     <span data-ttu-id="30340-127">![Domyślna aplikacja](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span><span class="sxs-lookup"><span data-stu-id="30340-127">![The default application](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span></span>  
  
     <span data-ttu-id="30340-128">Domyślna aplikacja definiuje zestaw klas w SampleDataSource.cs: SampleDataGroup i SampleDataItem, które są pochodnymi SampleDataCommon, które jest pochodną BindableBase.</span><span class="sxs-lookup"><span data-stu-id="30340-128">The default application defines a set of classes in SampleDataSource.cs: SampleDataGroup and SampleDataItem, both of which are derived from SampleDataCommon, which itself is derived from BindableBase.</span></span> <span data-ttu-id="30340-129">SampleDataGroup i SampleDataItem są powiązane z domyślnego widoku GridView.</span><span class="sxs-lookup"><span data-stu-id="30340-129">SampleDataGroup and SampleDataItem are bound to the default GridView.</span></span> <span data-ttu-id="30340-130">SampleDataSource.cs znajduje się w folderze DataModel w projekcie NetflixDemo.</span><span class="sxs-lookup"><span data-stu-id="30340-130">SampleDataSource.cs is located in the DataModel folder within the NetflixDemo project.</span></span> <span data-ttu-id="30340-131">Aplikacja wyświetla zgrupowaną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="30340-131">The application displays a grouped collection.</span></span> <span data-ttu-id="30340-132">Każda grupa zawiera dowolną liczbę elementów reprezentowana odpowiednio przez SampleDataGroup, SampleDataItem, a.</span><span class="sxs-lookup"><span data-stu-id="30340-132">Each group contains any number of items, represented by SampleDataGroup and SampleDataItem, respectively.</span></span> <span data-ttu-id="30340-133">Poprzedni zrzut ekranu zawiera grupę o nazwie grupy 1 tytuł i wszystkie elementy w grupie wyświetlane razem.</span><span class="sxs-lookup"><span data-stu-id="30340-133">In the previous screen shot you can see a group called Group Title 1 and all of the items in the group displayed together.</span></span>  
  
     <span data-ttu-id="30340-134">Strona główna aplikacji jest GroupedItemsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="30340-134">The main page of the application is GroupedItemsPage.xaml.</span></span> <span data-ttu-id="30340-135">Zawiera on element GridView wyświetlający przykładowe dane utworzone przez klasę SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="30340-135">It contains a GridView that displays the sample data created by the SampleDataSource.cs class.</span></span> <span data-ttu-id="30340-136">GroupedItemsPage jest ładowany przez App.xaml.cs w wywołaniu rootFrame.Navigate:</span><span class="sxs-lookup"><span data-stu-id="30340-136">The GroupedItemsPage is loaded by the App.xaml.cs in a call to rootFrame.Navigate:</span></span>  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     <span data-ttu-id="30340-137">Powoduje to GroupedItemsPage z myślą o uruchamianiu i jego LoadState metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="30340-137">This causes the GroupedItemsPage to be instantiated and it’s LoadState method is called.</span></span> <span data-ttu-id="30340-138">LoadState powoduje, że statycznego wystąpienia klas SampleDataSource ma zostać utworzony, który tworzy kolekcję obiektów SampleDataGroup.</span><span class="sxs-lookup"><span data-stu-id="30340-138">LoadState causes the static SampleDataSource instance to be created, which creates a collection of SampleDataGroup objects.</span></span> <span data-ttu-id="30340-139">Każdy obiekt SampleDataGroup zawiera kolekcję obiektów SampleDataItem.</span><span class="sxs-lookup"><span data-stu-id="30340-139">Each SampleDataGroup object contains a collection of SampleDataItem objects.</span></span> <span data-ttu-id="30340-140">LoadState są przechowywane w kolekcji obiektów SampleDataGroup w DefaultViewModel:</span><span class="sxs-lookup"><span data-stu-id="30340-140">LoadState stores the collection of SampleDataGroup objects in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="30340-141">Metody DefaultViewModel następnie jest powiązany z widoku GridView.</span><span class="sxs-lookup"><span data-stu-id="30340-141">The DefaultViewModel is then bound to the GridView.</span></span> <span data-ttu-id="30340-142">To jest przywoływany w pliku GroupedItemsPage.xaml podczas konfigurowania powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="30340-142">This is referenced in the GroupedItemsPage.xaml file when configuring the data binding.</span></span>  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     <span data-ttu-id="30340-143">CollectionViewSource jest używany jako serwer proxy dla obsługi grupowanych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="30340-143">The CollectionViewSource is used as a proxy for handling grouped collections.</span></span> <span data-ttu-id="30340-144">W przypadku powiązania iterację kolekcji obiektów SampleDataGroup, aby wypełnić widoku GridView.</span><span class="sxs-lookup"><span data-stu-id="30340-144">When binding occurs, it iterates through the collection of SampleDataGroup objects to populate the GridView.</span></span>  <span data-ttu-id="30340-145">Atrybut ItemsPath informuje CollectionViewSource, jakie właściwości dla każdego obiektu SampleDataGroup, aby znaleźć SampleDataItems zawiera.</span><span class="sxs-lookup"><span data-stu-id="30340-145">The ItemsPath attribute tells the CollectionViewSource what property on each SampleDataGroup object to use to find the SampleDataItems it contains.</span></span> <span data-ttu-id="30340-146">W takim przypadku każdy obiekt SampleDataGroup zawiera kolekcję TopItems SampleDataItem obiektów.</span><span class="sxs-lookup"><span data-stu-id="30340-146">In this case each SampleDataGroup object contains a TopItems collection of SampleDataItem objects.</span></span>  
  
     <span data-ttu-id="30340-147">Dla aplikacji Netflix filmy są pogrupowane według rodzaju.</span><span class="sxs-lookup"><span data-stu-id="30340-147">For the Netflix application, movies are grouped by genre.</span></span> <span data-ttu-id="30340-148">Dlatego aplikacji Wyświetla numer gatunkami muzyki i listy filmów w ramach tego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="30340-148">So the application displays a number of genres and a list of movies within that genre.</span></span>  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a><span data-ttu-id="30340-149">Dodawanie odwołania do usługi do usługi Netflix OData</span><span class="sxs-lookup"><span data-stu-id="30340-149">Add a Service Reference to the Netflix OData Service</span></span>  
  
1.  <span data-ttu-id="30340-150">Zanim firma Microsoft może wprowadzać żadnych wywołań do usługi Netflix OData musimy dodać odwołanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="30340-150">Before we can make any calls to the Netflix OData service we need to add a service reference.</span></span> <span data-ttu-id="30340-151">Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz opcję Dodaj odwołanie do usługi...</span><span class="sxs-lookup"><span data-stu-id="30340-151">Right-click the project in the Solution Explorer and select Add Service Reference…</span></span>  
  
     <span data-ttu-id="30340-152">![Dodaj odwołanie do usługi w oknie dialogowym](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span><span class="sxs-lookup"><span data-stu-id="30340-152">![Add Service Reference Dialog](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span></span>  
  
2.  <span data-ttu-id="30340-153">Wprowadź adres URL usługi Netflix OData na pasku adresu i kliknij Przejdź.</span><span class="sxs-lookup"><span data-stu-id="30340-153">Enter the URL for the Netflix OData service in the Address bar and click Go.</span></span> <span data-ttu-id="30340-154">Ustaw Namespace odwołania do usługi do Netflix, a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="30340-154">Set the Namespace of the service reference to Netflix and click OK.</span></span>  
  
     <span data-ttu-id="30340-155">![Dodaj błąd odwołania usługi](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span><span class="sxs-lookup"><span data-stu-id="30340-155">![Add Service Reference Error](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30340-156">Jeśli nie został jeszcze zainstalowany [WCF Data Services narzędzia dla aplikacji ze Sklepu Windows](http://go.microsoft.com/fwlink/p/?LinkId=266652), zostanie wyświetlony monit z następującym komunikatem, takie jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="30340-156">If you have not yet installed [WCF Data Services Tools for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652), you will be prompted with a message such as the one above.</span></span> <span data-ttu-id="30340-157">Należy pobrać i zainstalować narzędzia, do którego odwołuje się łącze, aby kontynuować.</span><span class="sxs-lookup"><span data-stu-id="30340-157">You will need to download and install the tools referenced in the link to continue.</span></span>  
  
 <span data-ttu-id="30340-158">Dodanie odwołania do usługi generuje silnie typizowanej klasy korzystające usługi danych WCF można przeanalizować OData zwrócony przez usługę Netflix OData.</span><span class="sxs-lookup"><span data-stu-id="30340-158">Adding a service reference generates strongly typed classes that WCF Data Services will use to parse the OData returned by the Netflix OData service.</span></span> <span data-ttu-id="30340-159">Klas zdefiniowanych w SampleDataSource.cs może być powiązana z widoku GridView, więc musimy przenoszenie danych do powiązania klas zdefiniowanych w SampleDataSource.cs wygenerowane klasy klienta OData.</span><span class="sxs-lookup"><span data-stu-id="30340-159">The classes defined in SampleDataSource.cs can be bound to the GridView so we need to transfer the data from the generated OData client classes into the bindable classes defined in SampleDataSource.cs.</span></span>  <span data-ttu-id="30340-160">Aby to zrobić, należy wprowadzić kilka zmian w modelu danych zdefiniowanych w SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="30340-160">In order to do this, we need to make some changes to the data model defined in SampleDataSource.cs.</span></span>  
  
#### <a name="update-the-data-model-for-the-application"></a><span data-ttu-id="30340-161">Aktualizacja modelu danych dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="30340-161">Update the data model for the application</span></span>  
  
1.  <span data-ttu-id="30340-162">Zastąp istniejący kod w SampleDataSource.cs kod z [tego gist](https://gist.github.com/3419288).</span><span class="sxs-lookup"><span data-stu-id="30340-162">Replace the existing code in SampleDataSource.cs with the code from [this gist](https://gist.github.com/3419288).</span></span> <span data-ttu-id="30340-163">Zaktualizowany kod dodaje metodę LoadMovies (do klasy klas SampleDataSource), która wykonuje kwerendy względem usługi Netflix OData i wypełnia listę gatunkami muzyki (allGroups) i w obrębie każdego rodzaju listy filmów.</span><span class="sxs-lookup"><span data-stu-id="30340-163">The updated code adds a LoadMovies method (to the SampleDataSource class)  that performs a query against the Netflix OData service and populates a list of genres (allGroups) and within each genre a list of movies.</span></span> <span data-ttu-id="30340-164">Klasa SampleDataGroup jest używana do reprezentowania określonego rodzaju i klasa SampleDataItem jest używana do reprezentowania filmu.</span><span class="sxs-lookup"><span data-stu-id="30340-164">The SampleDataGroup class is used to represent a genre and the SampleDataItem class is used to represent a movie.</span></span>  
  
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
  
     <span data-ttu-id="30340-165">[Wzorca asynchronicznego opartego na zadaniach](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) jest używany do asynchronicznie pobierania 300 (wykonaj) ostatnie (OrderByDescending) PG oceną (filmy kopię z Netflix gdzie).</span><span class="sxs-lookup"><span data-stu-id="30340-165">The [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) is used to asynchronously get 300 (Take) recent (OrderByDescending) PG-rated (Where) movies back from Netflix.</span></span> <span data-ttu-id="30340-166">Pozostała część kod tworzy SimpleDataItems i SimpleDataGroups z jednostkami, które zostały zwrócone w źródle strumieniowym OData.</span><span class="sxs-lookup"><span data-stu-id="30340-166">The rest of the code constructs SimpleDataItems and SimpleDataGroups from the entities that were returned in the OData feed.</span></span>  
  
     <span data-ttu-id="30340-167">Klasa klas SampleDataSource implementuje również metody proste wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="30340-167">The SampleDataSource class also implements a simple search method.</span></span> <span data-ttu-id="30340-168">W takim przypadku tak proste wyszukiwanie w pamięci filmów załadowany.</span><span class="sxs-lookup"><span data-stu-id="30340-168">In this case, it does a simple in-memory search of the loaded movies.</span></span>  
  
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
  
     <span data-ttu-id="30340-169">Również w SampleDataSource.cs klasy o nazwie ExtensionMethods jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="30340-169">Also in SampleDataSource.cs a class called ExtensionMethods is defined.</span></span> <span data-ttu-id="30340-170">Każda z tych metod rozszerzenia korzysta ze wzorca NACIŚNIJ umożliwia klas SampleDataSource, można wykonać zapytania OData bez blokowania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="30340-170">Each of these extension methods uses the TAP pattern to allow the SampleDataSource to execute an OData query without blocking the UI.</span></span> <span data-ttu-id="30340-171">Na przykład następujący kod używa metody Task.Factory.FromAsync do zaimplementowania NACIŚNIJ.</span><span class="sxs-lookup"><span data-stu-id="30340-171">For example, the following code uses the Task.Factory.FromAsync method to implement TAP.</span></span>  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     <span data-ttu-id="30340-172">Jak aplikacja domyślna strona główna aplikacji jest GroupedItemsPage.</span><span class="sxs-lookup"><span data-stu-id="30340-172">As in the default application, the main page of the application is GroupedItemsPage.</span></span> <span data-ttu-id="30340-173">Teraz, jednak Wyświetla filmy pobierane z Netflix pogrupowane według rodzaju.</span><span class="sxs-lookup"><span data-stu-id="30340-173">This time, however, it displays the movies retrieved from Netflix grouped by genre.</span></span>  <span data-ttu-id="30340-174">Podczas tworzenia wystąpienia klasy GroupedItemsPage jego LoadState — metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="30340-174">When the GroupedItemsPage is instantiated, its LoadState method is called.</span></span> <span data-ttu-id="30340-175">LoadState powoduje, że statycznego wystąpienia klas SampleDataSource, należy utworzyć nawiązywania połączenia z usługą Netflix OData zgodnie z opisem wcześniej.</span><span class="sxs-lookup"><span data-stu-id="30340-175">LoadState causes the static SampleDataSource instance to be created, making a call to the Netflix OData service as discussed previously.</span></span> <span data-ttu-id="30340-176">LoadState przechowuje kolekcji gatunkami muzyki (SampleDataGroup obiekty) w DefaultViewModel:</span><span class="sxs-lookup"><span data-stu-id="30340-176">LoadState stores the collection of genres (SampleDataGroup objects) in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="30340-177">Jak opisano wcześniej, DefaultViewModel jest następnie używany do wiązania danych do widoku GridView.</span><span class="sxs-lookup"><span data-stu-id="30340-177">As described previously, the DefaultViewModel is then used to bind the data to the GridView.</span></span>  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a><span data-ttu-id="30340-178">Dodaj umowy wyszukiwania umożliwiają aplikację do uczestnictwa w wyszukiwania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30340-178">Add a search contract to allow the application to participate in Windows search</span></span>  
  
1.  <span data-ttu-id="30340-179">Dodaj umowy wyszukiwania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30340-179">Add a search contract to the application.</span></span> <span data-ttu-id="30340-180">Umożliwia to aplikacji do integracji z wyników wyszukiwania systemu Windows 8.</span><span class="sxs-lookup"><span data-stu-id="30340-180">This allows the application to integrate with the Windows 8 search experience.</span></span> <span data-ttu-id="30340-181">Nazwa kontraktu wyszukiwania SearchResultsPage.xaml</span><span class="sxs-lookup"><span data-stu-id="30340-181">Name the search contract SearchResultsPage.xaml</span></span>  
  
     <span data-ttu-id="30340-182">![Dodaj umowy wyszukiwania](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span><span class="sxs-lookup"><span data-stu-id="30340-182">![Add a search contract](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span></span>  
  
2.  <span data-ttu-id="30340-183">Zmodyfikuj wiersza 58 SearchResultsPage.xaml.cs przez usunięcie osadzonych stawiać cudzysłów wokół queryText.</span><span class="sxs-lookup"><span data-stu-id="30340-183">Modify line 58 of SearchResultsPage.xaml.cs by removing the embedded quotes around queryText.</span></span>  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  <span data-ttu-id="30340-184">Wstaw następujące dwa wiersze kodu w wierszu 81 SearchResultsPage.xaml.cs można pobrać wyników wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="30340-184">Insert the following two lines of code at line 81 in SearchResultsPage.xaml.cs to retrieve the search results.</span></span>  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 <span data-ttu-id="30340-185">Gdy użytkownik wywołuje wyszukiwania systemu Windows, typów w terminu wyszukiwania i go dotyka pokaz Netflix ikonę aplikacji na pasku wyszukiwania, metodzie LoadState SearchResultsPage jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="30340-185">When a user invokes Windows search, types in a search term and then touches the Netflix Demo app icon in the search bar, the LoadState method of the SearchResultsPage is executed.</span></span> <span data-ttu-id="30340-186">Parametr nawigacji wysyłane do LoadState zawiera tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="30340-186">The navigation parameter sent to LoadState contains the query text.</span></span> <span data-ttu-id="30340-187">Następnie metoda Filter_SelectionChanged jest wywoływana, które, a następnie wywołuje metodę wyszukiwania w klasie klas SampleDataSource.</span><span class="sxs-lookup"><span data-stu-id="30340-187">Next the Filter_SelectionChanged method is called which then calls the Search method on the SampleDataSource class.</span></span> <span data-ttu-id="30340-188">Wyniki są zwracane, a następnie wyświetlane na stronie SearchResultsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="30340-188">The results are returned and displayed in the SearchResultsPage.xaml page.</span></span>  
  
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
  
 <span data-ttu-id="30340-189">Aby uzyskać więcej informacji na temat integracji wyszukiwania aplikacji, zobacz [wyszukiwania: integrowanie środowiska wyszukiwania systemu Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span><span class="sxs-lookup"><span data-stu-id="30340-189">For more information on integrating search into an application see, [Search: integrating into the Windows 8 search experience](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span></span>  
  
## <a name="run-the-application"></a><span data-ttu-id="30340-190">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="30340-190">Run the application</span></span>  
 <span data-ttu-id="30340-191">Uruchom aplikację, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="30340-191">Launch the application by pressing F5.</span></span> <span data-ttu-id="30340-192">Należy pamiętać, że potrwa kilka sekund do ładowania obrazów podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30340-192">Note that it will take a few seconds to load the images upon application launch.</span></span> <span data-ttu-id="30340-193">Ponadto pierwsza próba wyszukiwania nie może zwracać żadnych wyników.</span><span class="sxs-lookup"><span data-stu-id="30340-193">Also, your first search attempt may not return any results.</span></span> <span data-ttu-id="30340-194">W przypadku aplikacji rzeczywistych należy uwzględniać oba te problemy.</span><span class="sxs-lookup"><span data-stu-id="30340-194">In a real-world application, you would want to deal with both of these issues.</span></span>  
  
 <span data-ttu-id="30340-195">Aplikacja wywołuje usługę Netflix OData, odbiera dane w wygenerowane klasy klienta OData, a następnie przesyła dane do klasy powiązania danych (klas SampleDataSource, SampleDataGroup i SampleDataItem).</span><span class="sxs-lookup"><span data-stu-id="30340-195">The application calls the Netflix OData service, receives the data in the generated OData client classes and then transfers that data to bindable data classes (SampleDataSource, SampleDataGroup, and SampleDataItem).</span></span> <span data-ttu-id="30340-196">Aby powiązać dane z widoku GridView używa tych klas może być powiązana.</span><span class="sxs-lookup"><span data-stu-id="30340-196">It uses these bindable classes to bind the data to the GridView.</span></span> <span data-ttu-id="30340-197">Jeśli użytkownik nie zna działania można znaleźć XAML databinding [jak grupować elementy na liście lub siatki (aplikacje ze Sklepu Windows przy użyciu języka C# / VB/C++ i XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span><span class="sxs-lookup"><span data-stu-id="30340-197">If you are unfamiliar with how XAML databinding works see [How to group items in a list or grid (Windows Store apps using C#/VB/C++ and XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span></span>
