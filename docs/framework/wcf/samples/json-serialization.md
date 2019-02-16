---
title: Serializacja JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 2d1daa3388c49964430fe462ea92bf4ac310a974
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332016"
---
# <a name="json-serialization"></a><span data-ttu-id="98834-102">Serializacja JSON</span><span class="sxs-lookup"><span data-stu-id="98834-102">JSON Serialization</span></span>
<span data-ttu-id="98834-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> do serializacji i deserializacji danych w formacie JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="98834-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="98834-104">Ten mechanizm serializacji konwertuje dane JSON do wystąpień [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów i z powrotem na dane JSON.</span><span class="sxs-lookup"><span data-stu-id="98834-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="98834-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje te same typy jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="98834-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="98834-106">Format danych JSON jest szczególnie przydatne podczas pisania asynchronicznego języka JavaScript i XML (technologia AJAX)-stylów aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="98834-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="98834-107">Obsługa technologii AJAX w Windows Communication Foundation (WCF) została zoptymalizowana do użytku przy użyciu rozszerzeń ASP.NET AJAX, za pomocą formantu ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="98834-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="98834-108">Przykłady dotyczące używania usługi Windows Communication Foundation (WCF) przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="98834-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98834-109">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="98834-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="98834-110">W przykładzie użyto `Person` kontraktu danych zademonstrować serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="98834-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="98834-111">Do serializacji wystąpienia `Person` wpisz do formatu JSON, Utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pierwszy i użyj `WriteObject` metodę, aby zapisać dane JSON do strumienia.</span><span class="sxs-lookup"><span data-stu-id="98834-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="98834-112">Strumień pamięci zawiera prawidłowe dane JSON.</span><span class="sxs-lookup"><span data-stu-id="98834-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="98834-113">W przykładzie pokazano deserializacją z danymi w formacie JSON na obiekt.</span><span class="sxs-lookup"><span data-stu-id="98834-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="98834-114">Następnie przewiń strumienia i wywołanie `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="98834-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="98834-115">Badanie `p2` obiektu wykazuje, że dane JSON została przeprowadzona prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="98834-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98834-116">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="98834-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98834-117">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="98834-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98834-118">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="98834-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98834-119">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="98834-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="98834-120">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="98834-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="98834-121">Skompiluj rozwiązanie JsonSerialization.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="98834-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="98834-122">Uruchamianie wynikłej aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="98834-122">Run the resulting console application.</span></span>  
