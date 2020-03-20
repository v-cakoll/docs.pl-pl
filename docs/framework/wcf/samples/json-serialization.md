---
title: DataContractJsonSerializer próbki
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144633"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="c1284-102">DataContractJsonSerializer próbki</span><span class="sxs-lookup"><span data-stu-id="c1284-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="c1284-103">Ten przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>jest dla .</span><span class="sxs-lookup"><span data-stu-id="c1284-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="c1284-104">W przypadku większości scenariuszy, które obejmują serializację i deserializację JSON, zalecamy interfejsy API w [obszarze nazw System.Text.Json](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c1284-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="c1284-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>obsługuje te same <xref:System.Runtime.Serialization.DataContractSerializer>typy co .</span><span class="sxs-lookup"><span data-stu-id="c1284-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c1284-106">Format danych JSON jest szczególnie przydatny podczas pisania asynchronicznych aplikacji sieci Web w stylu JavaScript i XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="c1284-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="c1284-107">Obsługa ajax w programie Windows Communication Foundation (WCF) jest zoptymalizowana do użytku z ASP.NET AJAX za pośrednictwem formantu ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="c1284-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="c1284-108">Przykłady używania programu Windows Communication Foundation (WCF) z ASP.NET AJAX można znaleźć w [przykładzie próbek ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="c1284-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="c1284-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c1284-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="c1284-110">W przykładzie `Person` użyto umowy danych do wykazania serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="c1284-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="c1284-111">Aby serializować wystąpienie `Person` typu do JSON, utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pierwszy i użyj metody do zapisu `WriteObject` danych JSON do strumienia.</span><span class="sxs-lookup"><span data-stu-id="c1284-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="c1284-112">Strumień pamięci zawiera prawidłowe dane JSON.</span><span class="sxs-lookup"><span data-stu-id="c1284-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="c1284-113">Przykład demonstruje deserializacji z danych JSON do obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1284-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="c1284-114">Następnie przewiń strumień `ReadObject`i zadzwoń .</span><span class="sxs-lookup"><span data-stu-id="c1284-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="c1284-115">Badanie `p2` obiektu ujawnia, że dane JSON został poprawnie zdesializowany.</span><span class="sxs-lookup"><span data-stu-id="c1284-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c1284-116">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c1284-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c1284-117">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c1284-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c1284-118">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c1284-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c1284-119">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c1284-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c1284-120">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c1284-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="c1284-121">Zbuduj rozwiązanie JsonSerialization.sln zgodnie z opisem w [tworzenie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1284-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="c1284-122">Uruchom wynikową aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="c1284-122">Run the resulting console application.</span></span>  
