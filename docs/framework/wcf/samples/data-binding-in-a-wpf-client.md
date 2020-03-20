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
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Wiązanie danych w kliencie WPF (Windows Presentation Foundation)
W tym przykładzie pokazano użycie powiązania danych w kliencie programu Windows Presentation Foundation (WPF). W przykładzie jest używana usługa Windows Communication Foundation (WCF), która losowo generuje tablicę albumów w celu zwrócenia do klienta. Każdy album ma nazwę, cenę i listę utworów z albumu. Utwory z albumu mają nazwę i czas trwania. Informacje zwracane przez usługę są automatycznie powiązane z interfejsem użytkownika (UI) dostarczonym przez klienta Programu Windows Presentation Foundation (WPF).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Powiązanie danych umożliwia źródło danych, które mają być automatycznie powiązane z interfejsem użytkownika. Upraszcza to model programowania, ponieważ nie wymaga programowej aktualizacji każdego elementu interfejsu użytkownika danymi z obiektu danych lub tablicy obiektów danych. Obiekt można powiązać z pojedynczym elementem interfejsu użytkownika lub tablicą z `ListBox`formantem, który przyjmuje wiele danych wejściowych, takich jak . Poniższy kod pokazuje, jak `DataContext` powiązać dane z elementem interfejsu użytkownika.  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 W poprzednim przykładzie `DataContext` dla `grid` elementu `myPanel` układu o nazwie jest `GetAlbumList` ustawiona na dane zwracane przez metodę. Umożliwia `DataContext` elementy dziedziczyć informacje z ich elementów nadrzędnych o źródle danych, który jest używany do wiązania, a także inne cechy powiązania, takie jak ścieżka. Wiersz kodu musi być wykonywany za każdym razem, gdy dane na serwerze są aktualizowane. Na przykład jest wykonywany podczas inicjowania okna i po dodaniu nowego albumu.  
  
 W poniższym przykładowym kodzie `ListBox` XAML określa `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Określa to, że dane powiązane z elementem interfejsu użytkownika najwyższego poziomu jest również powiązany z tym formantem (czyli tablicą albumów). Ponadto określa `ItemTemplate="{StaticResource AlbumStyle}"` szablon danych, który ma być używany `ListBox`dla każdego elementu w pliku . Można również zdefiniować szablony danych, aby określić sposób formatowania danych. Te szablony danych mogą być ponownie wykorzystane dla innych elementów interfejsu użytkownika w aplikacji, zaletą jest to, że szablon danych jest zdefiniowany i utrzymywany w jednym miejscu.  
  
 Szablon `AlbumStyle` danych określa siatkę z `TextBlock`dwoma s obok siebie. Jeden określa nazwę albumu, a drugi liczbę utworów w albumie.  
  
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
  
 Poniższy kod XAML `ListBox`tworzy drugi .  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kod określa ścieżkę dla `ItemsSource`. Oznacza to, że dane powiązane z tym formantem nie są danymi najwyższego `Tracks`poziomu, ale właściwością danych najwyższego poziomu o nazwie . Ta właściwość reprezentuje tablicę utworów zawartych w albumie. Ponadto określono inną `DataTemplate` `TrackStyle` nazwę. Układ szablonu `TrackStyle` jest podobny do `AlbumStyle` szablonu, `TextBlock`ale s są powiązane z różnymi właściwościami. Dzieje się tak, ponieważ dwa szablony są używane z różnymi obiektami danych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
