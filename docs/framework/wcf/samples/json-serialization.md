---
title: Serializacja JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 364c5935dbbe087b413d28a033e0b5b569b02c9a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045547"
---
# <a name="json-serialization"></a><span data-ttu-id="e8c9b-102">Serializacja JSON</span><span class="sxs-lookup"><span data-stu-id="e8c9b-102">JSON Serialization</span></span>
<span data-ttu-id="e8c9b-103">Ten przykład pokazuje, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak używać do serializacji i deserializacji danych w formacie JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="e8c9b-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="e8c9b-104">Ten aparat serializacji konwertuje dane JSON na wystąpienia typów .NET Framework i z powrotem do danych JSON.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-104">This serialization engine converts JSON data into instances of .NET Framework types and back into JSON data.</span></span> <span data-ttu-id="e8c9b-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>obsługuje te same typy co <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="e8c9b-106">Format danych JSON jest szczególnie przydatny podczas pisania asynchronicznych aplikacji sieci Web w stylu JavaScript i XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="e8c9b-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="e8c9b-107">Obsługa technologii AJAX w programie Windows Communication Foundation (WCF) jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez kontrolkę ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="e8c9b-108">Przykłady użycia Windows Communication Foundation (WCF) z ASP.NET AJAX można znaleźć w przykładach [AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="e8c9b-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8c9b-109">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e8c9b-110">Przykład używa `Person` kontraktu danych w celu przedstawienia serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="e8c9b-111">Aby serializować wystąpienie `Person` typu do formatu JSON, należy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> utworzyć pierwszy i użyć `WriteObject` metody do zapisania danych JSON w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="e8c9b-112">Strumień pamięci zawiera prawidłowe dane JSON.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="e8c9b-113">Przykład demonstruje deserializacji z danych JSON do obiektu.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="e8c9b-114">Następnie przewiń strumień i Wywołaj `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="e8c9b-115">`p2` Badanie obiektu informuje o poprawnym deserializacji danych JSON.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e8c9b-116">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8c9b-117">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e8c9b-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e8c9b-118">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8c9b-119">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8c9b-120">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e8c9b-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="e8c9b-121">Skompiluj rozwiązanie JsonSerialization. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8c9b-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e8c9b-122">Uruchom utworzoną aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-122">Run the resulting console application.</span></span>  
