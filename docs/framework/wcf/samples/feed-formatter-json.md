---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 742d9be71d40a7f8ac15404c0d0ad573a570209d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501432"
---
# <a name="feed-formatter-json"></a><span data-ttu-id="fc9df-102">Program formatujący kanału informacyjnego (format JSON)</span><span class="sxs-lookup"><span data-stu-id="fc9df-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="fc9df-103">Ten przykład przedstawia sposób serializacji wystąpienia <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy w formacie JavaScript Object Notation (JSON) za pomocą niestandardowego <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fc9df-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="fc9df-104">Architektura próbki</span><span class="sxs-lookup"><span data-stu-id="fc9df-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="fc9df-105">Przykład implementuje klasy o nazwie `JsonFeedFormatter` dziedziczący po <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="fc9df-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="fc9df-106">`JsonFeedFormatter` Zależy od klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> do odczytywania i zapisywania danych w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="fc9df-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="fc9df-107">Wewnętrznie program formatujący używa niestandardowego zestawu typy kontraktu danych o nazwie `JsonSyndicationFeed` i `JsonSyndicationItem` kontrolujesz format danych JSON utworzony przez serializator.</span><span class="sxs-lookup"><span data-stu-id="fc9df-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="fc9df-108">Te szczegóły implementacji są ukryte przed użytkownikiem końcowym, umożliwiając wywołania ma zostać wykonane zgodności ze standardem <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klasy.</span><span class="sxs-lookup"><span data-stu-id="fc9df-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="fc9df-109">Zapisywanie źródła JSON</span><span class="sxs-lookup"><span data-stu-id="fc9df-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="fc9df-110">Pisanie JSON, źródła danych można wykonać za pomocą `JsonFeedFormatter` (zaimplementowana w tym przykładzie) z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="fc9df-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="fc9df-111">Odczytywanie źródło danych JSON</span><span class="sxs-lookup"><span data-stu-id="fc9df-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="fc9df-112">Uzyskiwanie <xref:System.ServiceModel.Syndication.SyndicationFeed> danych formacie strumienia JSON można wykonywać z `JsonFeedFormatter` Pokaż tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fc9df-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc9df-113">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="fc9df-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fc9df-114">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc9df-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fc9df-115">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc9df-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fc9df-116">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc9df-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc9df-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fc9df-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fc9df-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fc9df-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fc9df-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fc9df-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc9df-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fc9df-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="fc9df-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc9df-121">See Also</span></span>
