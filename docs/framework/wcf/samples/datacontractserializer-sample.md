---
title: Przykład elementu DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 07c6d3b10f2a0478f8fb3835f0b040668c5013ce
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600013"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="c0410-102">Przykład elementu DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="c0410-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="c0410-103">Przykład DataContractSerializer pokazuje <xref:System.Runtime.Serialization.DataContractSerializer> , który wykonuje ogólne usługi serializacji i deserializacji dla klas kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="c0410-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="c0410-104">Przykład tworzy `Record` obiekt, serializować go do strumienia pamięci i deserializacji strumień pamięci z powrotem do innego `Record` obiektu, aby pokazać użycie <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="c0410-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c0410-105">Następnie próbka serializować `Record` Obiekt przy użyciu binarnego składnika zapisywania, aby zademonstrować, jak moduł zapisujący ma wpływ na serializacji.</span><span class="sxs-lookup"><span data-stu-id="c0410-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0410-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c0410-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c0410-107">Kontrakt danych dla programu `Record` jest wyświetlany w następującym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c0410-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
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
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="c0410-108">Przykładowy kod tworzy `Record` obiekt o nazwie `record1` , a następnie wyświetla obiekt.</span><span class="sxs-lookup"><span data-stu-id="c0410-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="c0410-109">Następnie próbka używa <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji do `record1` strumienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="c0410-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="c0410-110">Następnie przykład używa <xref:System.Runtime.Serialization.DataContractSerializer> do deserializacji strumienia pamięci z powrotem do nowego `Record` obiektu i wyświetla go.</span><span class="sxs-lookup"><span data-stu-id="c0410-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="c0410-111">Domyślnie `DataContractSerializer` kodowanie obiektów do strumienia przy użyciu tekstowej reprezentacji XML.</span><span class="sxs-lookup"><span data-stu-id="c0410-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="c0410-112">Można jednak mieć wpływ na kodowanie kodu XML przez przekazanie w innym składniku zapisywania.</span><span class="sxs-lookup"><span data-stu-id="c0410-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="c0410-113">Przykład tworzy binarny moduł zapisujący przez wywołanie <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> .</span><span class="sxs-lookup"><span data-stu-id="c0410-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="c0410-114">Następnie przekazuje moduł zapisujący i obiekt rekordu do serializatora podczas wywoływania <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> .</span><span class="sxs-lookup"><span data-stu-id="c0410-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="c0410-115">Na koniec przykład opróżnia składnik zapisywania i raporty o długości strumieni.</span><span class="sxs-lookup"><span data-stu-id="c0410-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="c0410-116">Po uruchomieniu przykładu zostanie wyświetlony oryginalny rekord i deserializowany rekord, po którym następuje porównanie długości kodowania tekstu i kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="c0410-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="c0410-117">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="c0410-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c0410-118">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="c0410-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c0410-119">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0410-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c0410-120">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0410-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c0410-121">Aby uruchomić przykład, uruchom klienta z wiersza polecenia, wpisując client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="c0410-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c0410-122">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c0410-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c0410-123">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c0410-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c0410-124">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c0410-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c0410-125">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c0410-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
