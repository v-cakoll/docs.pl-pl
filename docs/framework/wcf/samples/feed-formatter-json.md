---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 350e07ad37b09f39fc709e20d8f73a41f9d01f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183651"
---
# <a name="feed-formatter-json"></a><span data-ttu-id="5b23a-102">Program formatujący kanału informacyjnego (format JSON)</span><span class="sxs-lookup"><span data-stu-id="5b23a-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="5b23a-103">W tym przykładzie pokazano, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> serializować wystąpienie klasy w formacie Notacji <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiektu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>JavaScript (JSON) przy użyciu niestandardowego i .</span><span class="sxs-lookup"><span data-stu-id="5b23a-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="5b23a-104">Architektura próbki</span><span class="sxs-lookup"><span data-stu-id="5b23a-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="5b23a-105">Przykład implementuje klasę `JsonFeedFormatter` o nazwie, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>która dziedziczy po .</span><span class="sxs-lookup"><span data-stu-id="5b23a-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="5b23a-106">Klasa `JsonFeedFormatter` opiera się <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> na do odczytu i zapisu danych w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="5b23a-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="5b23a-107">Wewnętrznie formater używa niestandardowego zestawu typów kontraktów `JsonSyndicationFeed` `JsonSyndicationItem` danych o nazwie i do kontrolowania formatu danych JSON produkowanych przez serializatora.</span><span class="sxs-lookup"><span data-stu-id="5b23a-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="5b23a-108">Te szczegóły implementacji są ukryte przed użytkownikiem końcowym, <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> dzięki czemu wywołania mają być wykonane względem standardu i klas.</span><span class="sxs-lookup"><span data-stu-id="5b23a-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="5b23a-109">Pisanie kanałów JSON</span><span class="sxs-lookup"><span data-stu-id="5b23a-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="5b23a-110">Pisanie źródła danych JSON można wykonać `JsonFeedFormatter` przy użyciu (zaimplementowane w tym przykładzie) z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak pokazano w poniższym kodzie przykładowym.</span><span class="sxs-lookup"><span data-stu-id="5b23a-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
```csharp  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="5b23a-111">Czytanie kanału JSON</span><span class="sxs-lookup"><span data-stu-id="5b23a-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="5b23a-112">Uzyskanie <xref:System.ServiceModel.Syndication.SyndicationFeed> z strumienia danych w formacie JSON można wykonać `JsonFeedFormatter` za pomocą as show w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5b23a-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5b23a-113">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="5b23a-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5b23a-114">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b23a-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5b23a-115">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b23a-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5b23a-116">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b23a-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b23a-117">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5b23a-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5b23a-118">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="5b23a-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5b23a-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5b23a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b23a-120">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5b23a-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
