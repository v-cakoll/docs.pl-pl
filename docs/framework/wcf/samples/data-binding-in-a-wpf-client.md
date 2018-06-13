---
title: Powiązywanie danych w kliencie WPF (Windows Presentation Foundation)
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 225bdedb67e218092ff3369d4fe742c4fc897fc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502549"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="d2f2d-102">Powiązywanie danych w kliencie WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="d2f2d-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="d2f2d-103">W tym przykładzie przedstawiono używanie powiązania danych w kliencie systemu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="d2f2d-104">W przykładzie użyto losowo generuje tablicę albumów do zwrócenia do klienta usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="d2f2d-105">Każdego albumu ma nazwę, ceny i listy ścieżek albumu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="d2f2d-106">Śledzi albumu ma nazwę i czas trwania.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="d2f2d-107">Informacje, które są zwracane przez usługę automatycznie jest powiązana z dostarczonym przez klienta Windows Presentation Foundation (WPF) interfejsu użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2f2d-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d2f2d-109">Powiązanie danych umożliwia źródła danych może być automatycznie powiązane z interfejsem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="d2f2d-110">Upraszcza to model programowania, ponieważ nie wymaga programowane aktualizowanie każdego elementu interfejsu użytkownika przy użyciu danych z obiektu danych lub tablicę obiektów danych.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="d2f2d-111">Można powiązać obiektu pojedynczy element interfejsu użytkownika lub tablicy do formantu, który przyjmuje wielu danych wejściowych, takich jak `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="d2f2d-112">Poniższy kod przedstawia sposób powiązania danych do `DataContext` elementu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="d2f2d-113">W poprzednim przykładzie `DataContext` dla `grid` układu elementu o nazwie `myPanel` ma ustawioną wartość danych zwróconych przez `GetAlbumList` metody.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="d2f2d-114">`DataContext` Umożliwia elementom dziedziczenie informacji z ich elementów nadrzędnych dotyczące źródła danych, która jest używana do wiązania, a także innych charakterystyk powiązania, takich jak ścieżka.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="d2f2d-115">Wiersz kodu musi zostać wykonana w każdej aktualizacji danych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="d2f2d-116">Na przykład jest wykonywany po zainicjowaniu okna i po dodaniu nowego albumu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="d2f2d-117">W poniższym przykładowym kodzie XAML `ListBox` Określa `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="d2f2d-118">To ustawienie określa powiązany element interfejsu użytkownika najwyższego poziomu jest także powiązany z danymi do tego formantu (to znaczy tablicę albumów).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="d2f2d-119">Ponadto `ItemTemplate="{StaticResource AlbumStyle}"` Określa szablon danych, który ma być używany dla każdego elementu w `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="d2f2d-120">Istnieje również możliwość definiowania szablonów danych, aby określić sposób formatowania danych.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="d2f2d-121">Te dane, które można ponownie użyć szablonów innych elementów interfejsu użytkownika w aplikacji, zaletą jest to, że szablon danych jest zdefiniowany i jest utrzymywany w jednym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="d2f2d-122">`AlbumStyle` Szablon danych wychodzi poza siatkę z dwóch `TextBlock`s obok siebie.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="d2f2d-123">Jeden Określa nazwę albumu i innych liczbę ścieżek w albumu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="d2f2d-124">Poniższy kod XAML tworzy drugi `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="d2f2d-125">Kod określa ścieżkę do `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="d2f2d-126">Oznacza to, że danych powiązanego z tym formantem nie jest danych najwyższego poziomu, ale właściwość danych najwyższego poziomu o nazwie `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="d2f2d-127">Ta właściwość reprezentuje tablicę ścieżek zawartych w albumu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="d2f2d-128">Ponadto innej `DataTemplate` o nazwie `TrackStyle` jest określona.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="d2f2d-129">Układ `TrackStyle` szablon jest podobny do `AlbumStyle` szablonu, ale `TextBlock`s są powiązane z innej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="d2f2d-130">Jest to spowodowane dwa szablony są używane z obiektami innych danych.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d2f2d-131">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d2f2d-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d2f2d-132">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d2f2d-133">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d2f2d-134">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2f2d-135">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d2f2d-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d2f2d-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d2f2d-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d2f2d-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d2f2d-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a><span data-ttu-id="d2f2d-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2f2d-139">See Also</span></span>
