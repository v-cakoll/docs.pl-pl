---
title: "Przykład elementu DataContractSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
caps.latest.revision: "37"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2cb8ae40cb62c65bf6dbd394055fffadd7202f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="6c0a5-102">Przykład elementu DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="6c0a5-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="6c0a5-103">Przedstawiono przykład elementu DataContractSerializer <xref:System.Runtime.Serialization.DataContractSerializer>, który wykonuje ogólne serializacji i deserializacji usług danych klasy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="6c0a5-104">Tworzy próbki `Record` obiektu, serializuje go do strumienia pamięci i deserializuje strumienia pamięci do innego `Record` obiektu przedstawiają sposób używania <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="6c0a5-105">Następnie wykonuje serializację próbki `Record` aby zademonstrować wpływ twórcę serializacji przy użyciu binarne składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c0a5-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6c0a5-107">Dla kontraktu danych `Record` jest wyświetlany w następujący przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return string.Format("Record: {0} {1} {2} = {3}", n1,  
            operation, n2, result);  
    }  
}  
```  
  
 <span data-ttu-id="6c0a5-108">Przykładowy kod tworzy `Record` obiektu o nazwie `record1` następnie wyświetla obiektu.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="6c0a5-109">Następnie używa próbki <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji `record1` do strumienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="6c0a5-110">Następnie używa próbki <xref:System.Runtime.Serialization.DataContractSerializer> do deserializacji strumienia pamięci do nowego `Record` obiektów i wyświetla je.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="6c0a5-111">Domyślnie `DataContractSerializer` koduje obiektów w strumieniu przy użyciu tekstową reprezentację XML.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="6c0a5-112">Jednak możesz wywrzeć wpływ Kodowanie XML przez przekazywanie inny edytor.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="6c0a5-113">Przykład tworzy binarne składnika zapisywania przez wywołanie metody <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="6c0a5-114">Następnie przekazuje twórcę i obiekt rekordu do serializatora gdy wywołuje <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="6c0a5-115">Na koniec próbki opróżnia twórcę i raport dotyczący długość strumienia.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="6c0a5-116">Po uruchomieniu próbki rekordzie oryginalnym i rekord zdeserializowany są wyświetlane, następuje porównanie między długość kodowanie tekstu i kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="6c0a5-117">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6c0a5-118">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="6c0a5-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6c0a5-119">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c0a5-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6c0a5-120">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c0a5-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6c0a5-121">Aby uruchomić przykład, uruchom klienta z wiersza polecenia, wpisując client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c0a5-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c0a5-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="6c0a5-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c0a5-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c0a5-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6c0a5-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a><span data-ttu-id="6c0a5-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c0a5-126">See Also</span></span>
