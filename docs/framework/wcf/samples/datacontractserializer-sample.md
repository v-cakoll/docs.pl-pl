---
title: Przykład elementu DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 5e1a471cc4cc43b2aa36143eeecc18f7ec17b81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183778"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="c523a-102">Przykład elementu DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="c523a-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="c523a-103">Przykład DataContractSerializer pokazuje <xref:System.Runtime.Serialization.DataContractSerializer>, który wykonuje ogólne usługi serializacji i deserializacji dla klas kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="c523a-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="c523a-104">Próbka tworzy `Record` obiekt, serializuje go do strumienia pamięci i deserializes strumienia pamięci z powrotem do innego `Record` obiektu, aby zademonstrować użycie <xref:System.Runtime.Serialization.DataContractSerializer>. .</span><span class="sxs-lookup"><span data-stu-id="c523a-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c523a-105">Następnie próbka serializuje `Record` obiekt przy użyciu modułu zapisującego binarnego, aby zademonstrować, jak moduł zapisujący wpływa na serializację.</span><span class="sxs-lookup"><span data-stu-id="c523a-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c523a-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c523a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c523a-107">Kontrakt danych `Record` dla jest pokazany w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c523a-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c523a-108">Przykładowy kod `Record` tworzy `record1` obiekt o nazwie, a następnie wyświetla obiekt.</span><span class="sxs-lookup"><span data-stu-id="c523a-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="c523a-109">Następnie używa <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji `record1` w strumieniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="c523a-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="c523a-110">Następnie w próbce <xref:System.Runtime.Serialization.DataContractSerializer> używa do deserializacji strumienia `Record` pamięci z powrotem do nowego obiektu i wyświetla go.</span><span class="sxs-lookup"><span data-stu-id="c523a-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="c523a-111">Domyślnie `DataContractSerializer` koduje obiekty do strumienia przy użyciu tekstowej reprezentacji XML.</span><span class="sxs-lookup"><span data-stu-id="c523a-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="c523a-112">Można jednak wpływać na kodowanie pliku XML, przekazując w innym modułze zapisującego.</span><span class="sxs-lookup"><span data-stu-id="c523a-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="c523a-113">Przykład tworzy moduł zapisujący <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>binarny przez wywołanie .</span><span class="sxs-lookup"><span data-stu-id="c523a-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="c523a-114">Następnie przekazuje moduł zapisujący i obiekt rekordu do <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>serializatora, gdy wywołuje .</span><span class="sxs-lookup"><span data-stu-id="c523a-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="c523a-115">Na koniec przykład opróżnia moduł zapisujący i raportuje długość strumieni.</span><span class="sxs-lookup"><span data-stu-id="c523a-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="c523a-116">Po uruchomieniu próbki wyświetlany jest oryginalny rekord i rekord deserialnizowany, po którym następuje porównanie długości kodowania tekstu z kodowaniem binarnym.</span><span class="sxs-lookup"><span data-stu-id="c523a-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="c523a-117">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c523a-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c523a-118">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c523a-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c523a-119">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c523a-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c523a-120">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c523a-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c523a-121">Aby uruchomić przykład, uruchom klienta z wiersza polecenia, wpisując polecenie client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="c523a-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c523a-122">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c523a-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c523a-123">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c523a-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c523a-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c523a-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c523a-125">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c523a-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
