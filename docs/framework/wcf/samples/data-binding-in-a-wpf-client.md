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
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Powiązywanie danych w kliencie WPF (Windows Presentation Foundation)
W tym przykładzie przedstawiono używanie powiązania danych w kliencie systemu Windows Presentation Foundation (WPF). W przykładzie użyto losowo generuje tablicę albumów do zwrócenia do klienta usługi Windows Communication Foundation (WCF). Każdego albumu ma nazwę, ceny i listy ścieżek albumu. Śledzi albumu ma nazwę i czas trwania. Informacje, które są zwracane przez usługę automatycznie jest powiązana z dostarczonym przez klienta Windows Presentation Foundation (WPF) interfejsu użytkownika (UI).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Powiązanie danych umożliwia źródła danych może być automatycznie powiązane z interfejsem użytkownika. Upraszcza to model programowania, ponieważ nie wymaga programowane aktualizowanie każdego elementu interfejsu użytkownika przy użyciu danych z obiektu danych lub tablicę obiektów danych. Można powiązać obiektu pojedynczy element interfejsu użytkownika lub tablicy do formantu, który przyjmuje wielu danych wejściowych, takich jak `ListBox`. Poniższy kod przedstawia sposób powiązania danych do `DataContext` elementu interfejsu użytkownika.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 W poprzednim przykładzie `DataContext` dla `grid` układu elementu o nazwie `myPanel` ma ustawioną wartość danych zwróconych przez `GetAlbumList` metody. `DataContext` Umożliwia elementom dziedziczenie informacji z ich elementów nadrzędnych dotyczące źródła danych, która jest używana do wiązania, a także innych charakterystyk powiązania, takich jak ścieżka. Wiersz kodu musi zostać wykonana w każdej aktualizacji danych na serwerze. Na przykład jest wykonywany po zainicjowaniu okna i po dodaniu nowego albumu.  
  
 W poniższym przykładowym kodzie XAML `ListBox` Określa `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 To ustawienie określa powiązany element interfejsu użytkownika najwyższego poziomu jest także powiązany z danymi do tego formantu (to znaczy tablicę albumów). Ponadto `ItemTemplate="{StaticResource AlbumStyle}"` Określa szablon danych, który ma być używany dla każdego elementu w `ListBox`. Istnieje również możliwość definiowania szablonów danych, aby określić sposób formatowania danych. Te dane, które można ponownie użyć szablonów innych elementów interfejsu użytkownika w aplikacji, zaletą jest to, że szablon danych jest zdefiniowany i jest utrzymywany w jednym miejscu.  
  
 `AlbumStyle` Szablon danych wychodzi poza siatkę z dwóch `TextBlock`s obok siebie. Jeden Określa nazwę albumu i innych liczbę ścieżek w albumu.  
  
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
  
 Poniższy kod XAML tworzy drugi `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kod określa ścieżkę do `ItemsSource`. Oznacza to, że danych powiązanego z tym formantem nie jest danych najwyższego poziomu, ale właściwość danych najwyższego poziomu o nazwie `Tracks`. Ta właściwość reprezentuje tablicę ścieżek zawartych w albumu. Ponadto innej `DataTemplate` o nazwie `TrackStyle` jest określona. Układ `TrackStyle` szablon jest podobny do `AlbumStyle` szablonu, ale `TextBlock`s są powiązane z innej właściwości. Jest to spowodowane dwa szablony są używane z obiektami innych danych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a>Zobacz też
