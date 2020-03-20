---
title: Wiązanie danych w kliencie WPF (Windows Presentation Foundation)
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183820"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="e5c66-102">Wiązanie danych w kliencie WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="e5c66-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="e5c66-103">W tym przykładzie pokazano użycie powiązania danych w kliencie programu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e5c66-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="e5c66-104">W przykładzie jest używana usługa Windows Communication Foundation (WCF), która losowo generuje tablicę albumów w celu zwrócenia do klienta.</span><span class="sxs-lookup"><span data-stu-id="e5c66-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="e5c66-105">Każdy album ma nazwę, cenę i listę utworów z albumu.</span><span class="sxs-lookup"><span data-stu-id="e5c66-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="e5c66-106">Utwory z albumu mają nazwę i czas trwania.</span><span class="sxs-lookup"><span data-stu-id="e5c66-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="e5c66-107">Informacje zwracane przez usługę są automatycznie powiązane z interfejsem użytkownika (UI) dostarczonym przez klienta Programu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e5c66-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5c66-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e5c66-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e5c66-109">Powiązanie danych umożliwia źródło danych, które mają być automatycznie powiązane z interfejsem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5c66-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="e5c66-110">Upraszcza to model programowania, ponieważ nie wymaga programowej aktualizacji każdego elementu interfejsu użytkownika danymi z obiektu danych lub tablicy obiektów danych.</span><span class="sxs-lookup"><span data-stu-id="e5c66-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="e5c66-111">Obiekt można powiązać z pojedynczym elementem interfejsu użytkownika lub tablicą z `ListBox`formantem, który przyjmuje wiele danych wejściowych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="e5c66-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="e5c66-112">Poniższy kod pokazuje, jak `DataContext` powiązać dane z elementem interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5c66-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="e5c66-113">W poprzednim przykładzie `DataContext` dla `grid` elementu `myPanel` układu o nazwie jest `GetAlbumList` ustawiona na dane zwracane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="e5c66-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="e5c66-114">Umożliwia `DataContext` elementy dziedziczyć informacje z ich elementów nadrzędnych o źródle danych, który jest używany do wiązania, a także inne cechy powiązania, takie jak ścieżka.</span><span class="sxs-lookup"><span data-stu-id="e5c66-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="e5c66-115">Wiersz kodu musi być wykonywany za każdym razem, gdy dane na serwerze są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="e5c66-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="e5c66-116">Na przykład jest wykonywany podczas inicjowania okna i po dodaniu nowego albumu.</span><span class="sxs-lookup"><span data-stu-id="e5c66-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="e5c66-117">W poniższym przykładowym kodzie `ListBox` XAML określa `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="e5c66-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="e5c66-118">Określa to, że dane powiązane z elementem interfejsu użytkownika najwyższego poziomu jest również powiązany z tym formantem (czyli tablicą albumów).</span><span class="sxs-lookup"><span data-stu-id="e5c66-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="e5c66-119">Ponadto określa `ItemTemplate="{StaticResource AlbumStyle}"` szablon danych, który ma być używany `ListBox`dla każdego elementu w pliku .</span><span class="sxs-lookup"><span data-stu-id="e5c66-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="e5c66-120">Można również zdefiniować szablony danych, aby określić sposób formatowania danych.</span><span class="sxs-lookup"><span data-stu-id="e5c66-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="e5c66-121">Te szablony danych mogą być ponownie wykorzystane dla innych elementów interfejsu użytkownika w aplikacji, zaletą jest to, że szablon danych jest zdefiniowany i utrzymywany w jednym miejscu.</span><span class="sxs-lookup"><span data-stu-id="e5c66-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="e5c66-122">Szablon `AlbumStyle` danych określa siatkę z `TextBlock`dwoma s obok siebie.</span><span class="sxs-lookup"><span data-stu-id="e5c66-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="e5c66-123">Jeden określa nazwę albumu, a drugi liczbę utworów w albumie.</span><span class="sxs-lookup"><span data-stu-id="e5c66-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="e5c66-124">Poniższy kod XAML `ListBox`tworzy drugi .</span><span class="sxs-lookup"><span data-stu-id="e5c66-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="e5c66-125">Kod określa ścieżkę dla `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="e5c66-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="e5c66-126">Oznacza to, że dane powiązane z tym formantem nie są danymi najwyższego `Tracks`poziomu, ale właściwością danych najwyższego poziomu o nazwie .</span><span class="sxs-lookup"><span data-stu-id="e5c66-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="e5c66-127">Ta właściwość reprezentuje tablicę utworów zawartych w albumie.</span><span class="sxs-lookup"><span data-stu-id="e5c66-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="e5c66-128">Ponadto określono inną `DataTemplate` `TrackStyle` nazwę.</span><span class="sxs-lookup"><span data-stu-id="e5c66-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="e5c66-129">Układ szablonu `TrackStyle` jest podobny do `AlbumStyle` szablonu, `TextBlock`ale s są powiązane z różnymi właściwościami.</span><span class="sxs-lookup"><span data-stu-id="e5c66-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="e5c66-130">Dzieje się tak, ponieważ dwa szablony są używane z różnymi obiektami danych.</span><span class="sxs-lookup"><span data-stu-id="e5c66-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e5c66-131">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="e5c66-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e5c66-132">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5c66-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e5c66-133">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5c66-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e5c66-134">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5c66-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e5c66-135">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e5c66-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e5c66-136">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e5c66-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e5c66-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e5c66-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5c66-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5c66-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
