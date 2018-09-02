---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: bc73ae11f66d2c325fab274f8deec11355ce8b99
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407285"
---
# <a name="feed-formatter-json"></a>Program formatujący kanału informacyjnego (format JSON)
Ten przykład pokazuje, jak do serializacji wystąpienia <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy w formacie JavaScript Object Notation (JSON) za pomocą niestandardowego <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Architektura próbki  
 Przykład implementuje klasę o nazwie `JsonFeedFormatter` tej, która dziedziczy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. `JsonFeedFormatter` Zależy od klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> na odczytywanie i zapisywanie danych w formacie JSON. Wewnętrznie, program formatujący używa niestandardowego zestawu typy kontraktu danych o nazwie `JsonSyndicationFeed` i `JsonSyndicationItem` kontrolujesz format danych JSON utworzony przez element serializujący. Te szczegóły wdrożenia są ukryte przed użytkownika końcowego, umożliwiając wywołania zostać wykonane w stosunku do standardowych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klasy.  
  
## <a name="writing-json-feeds"></a>Źródła danych JSON zapisu  
 Zapisywanie kanału informacyjnego JSON można osiągnąć za pomocą `JsonFeedFormatter` (zaimplementowany w tym przykładzie) przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak pokazano w poniższym przykładowym kodzie.  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>Odczytywanie źródła danych JSON  
 Uzyskiwanie <xref:System.ServiceModel.Syndication.SyndicationFeed> dane sformatowane strumienia JSON można osiągnąć za pomocą `JsonFeedFormatter` tak jak pokazano w poniższym kodzie.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a>Zobacz też
