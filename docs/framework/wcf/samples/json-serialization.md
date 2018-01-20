---
title: Serializacja JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d87dd0f22473015ba51d7be996106a57c4708a67
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="json-serialization"></a><span data-ttu-id="aa174-102">Serializacja JSON</span><span class="sxs-lookup"><span data-stu-id="aa174-102">JSON Serialization</span></span>
<span data-ttu-id="aa174-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> do serializowania i deserializowania danych w formacie JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="aa174-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="aa174-104">Ten aparat serializacji konwertuje dane JSON na wystąpień [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów i z powrotem na dane JSON.</span><span class="sxs-lookup"><span data-stu-id="aa174-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="aa174-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>obsługuje te same typy jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="aa174-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="aa174-106">Format danych JSON jest szczególnie przydatne podczas zapisywania asynchronicznego JavaScript i XML (AJAX) — styl aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aa174-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="aa174-107">Obsługa interfejsu AJAX w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX, za pomocą formantu ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="aa174-107">AJAX support in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="aa174-108">Przykłady dotyczące używania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="aa174-108">For examples of how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa174-109">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="aa174-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="aa174-110">W przykładzie użyto `Person` kontraktu danych zademonstrować serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="aa174-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  
  
```  
[DataContract]  
    class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
```  
  
 <span data-ttu-id="aa174-111">Do serializacji wystąpienia `Person` typu do formatu JSON, Utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pierwszy i użyj `WriteObject` metody do zapisu danych JSON strumienia.</span><span class="sxs-lookup"><span data-stu-id="aa174-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  
  
```  
Person p = new Person();  
//Set up Person object...  
MemoryStream stream1 = new MemoryStream();  
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
ser.WriteObject(stream1, p);  
```  
  
 <span data-ttu-id="aa174-112">Strumienia pamięci zawiera poprawne dane JSON.</span><span class="sxs-lookup"><span data-stu-id="aa174-112">The memory stream contains valid JSON data.</span></span>  
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="aa174-113">W przykładzie pokazano, podczas deserializacji danych JSON na obiekt.</span><span class="sxs-lookup"><span data-stu-id="aa174-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="aa174-114">Następnie rewind strumienia i wywołania `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="aa174-114">You then rewind the stream and call `ReadObject`.</span></span>  
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 <span data-ttu-id="aa174-115">Badanie `p2` obiektu wykazuje, że dane JSON została prawidłowo zdeserializowana.</span><span class="sxs-lookup"><span data-stu-id="aa174-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa174-116">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="aa174-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa174-117">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="aa174-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aa174-118">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="aa174-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa174-119">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="aa174-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa174-120">Aby skonfigurować, tworzenie i uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="aa174-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="aa174-121">Skompiluj rozwiązanie JsonSerialization.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa174-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="aa174-122">Uruchom wynikowej aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="aa174-122">Run the resulting console application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa174-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa174-123">See Also</span></span>
