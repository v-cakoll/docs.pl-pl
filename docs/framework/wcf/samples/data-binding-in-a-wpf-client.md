---
title: Powiązywanie danych w kliencie WPF (Windows Presentation Foundation)
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 467a81c3f574137bc95390f70d6913a532da6ffe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626904"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Powiązywanie danych w kliencie WPF (Windows Presentation Foundation)
Niniejszy przykład pokazuje użycie powiązanie danych w kliencie Windows Presentation Foundation (WPF). W przykładzie użyto usługi Windows Communication Foundation (WCF), który losowo generuje tablicę ze zdjęciami, aby powrócić do klienta. Każdego albumu ma nazwę, cenę i listę ścieżek albumu. Śledzi albumu mają nazwy i czasu trwania. Informacje, które są zwracane przez usługę jest automatycznie powiązany z interfejsu użytkownika (UI), dostarczonego przez klienta programu Windows Presentation Foundation (WPF).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Powiązanie danych umożliwia źródła danych może być automatycznie powiązane z interfejsem użytkownika. Upraszcza to model programowania, ponieważ nie wymaga programowe aktualizowanie każdego elementu interfejsu użytkownika przy użyciu danych z obiektu danych lub użyj tablicy obiektów danych. Można powiązać obiektu pojedynczy element interfejsu użytkownika lub tablica do kontroli, która przyjmuje wielu danych wejściowych, takich jak `ListBox`. Poniższy kod pokazuje jak powiązać dane `DataContext` elementu interfejsu użytkownika.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 W poprzednim przykładzie `DataContext` dla `grid` układu elementu o nazwie `myPanel` jest ustawiona na dane zwrócone przez `GetAlbumList` metody. `DataContext` Umożliwia elementom dziedziczenie informacji z ich źródła danych, która jest używana do powiązania, a także innych charakterystyk powiązania, takich jak ścieżka elementów nadrzędnych. Musi zostać wykonany wiersz kodu, za każdym razem, gdy dane na serwerze są aktualizowane. Na przykład jest wykonywany, gdy okno jest inicjowany, i po dodaniu nowego albumu.  
  
 W poniższym przykładowym kodzie XAML `ListBox` Określa `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 To ustawienie określa, powiązany element najwyższego poziomu interfejsu użytkownika jest również powiązany z danymi do tego formantu (czyli tablicę albumów). Ponadto `ItemTemplate="{StaticResource AlbumStyle}"` Określa szablon danych, który ma być używany dla każdego elementu w `ListBox`. Można również definiować szablony danych, aby określić sposób formatowania danych. Te dane, które szablony mogą być ponownie używane dla innych elementów interfejsu użytkownika w aplikacji, ma tę zaletę, szablon danych jest zdefiniowany i jest utrzymywany w jednym miejscu.  
  
 `AlbumStyle` Szablon danych wykracza poza siatkę przy użyciu dwóch `TextBlock`s obok siebie. Jeden Określa nazwę Album i innych liczbę ścieżek w albumu.  
  
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
  
 Kod ten określa ścieżkę do `ItemsSource`. To oznacza, że dane powiązane z tej kontrolki jest danych najwyższego poziomu, ale właściwość danych najwyższego poziomu o nazwie `Tracks`. Ta właściwość reprezentuje tablicę ścieżek zawartych w albumu. Ponadto inny `DataTemplate` o nazwie `TrackStyle` jest określony. Układ `TrackStyle` szablon jest podobny do `AlbumStyle` szablonu, ale `TextBlock`s są powiązane z różnymi właściwościami. Jest to spowodowane dwa szablony są używane z różnymi danymi obiektów.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a>Zobacz także
