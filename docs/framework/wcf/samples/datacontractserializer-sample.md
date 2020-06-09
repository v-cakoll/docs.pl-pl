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
# <a name="datacontractserializer-sample"></a>Przykład elementu DataContractSerializer
Przykład DataContractSerializer pokazuje <xref:System.Runtime.Serialization.DataContractSerializer> , który wykonuje ogólne usługi serializacji i deserializacji dla klas kontraktu danych. Przykład tworzy `Record` obiekt, serializować go do strumienia pamięci i deserializacji strumień pamięci z powrotem do innego `Record` obiektu, aby pokazać użycie <xref:System.Runtime.Serialization.DataContractSerializer> . Następnie próbka serializować `Record` Obiekt przy użyciu binarnego składnika zapisywania, aby zademonstrować, jak moduł zapisujący ma wpływ na serializacji.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt danych dla programu `Record` jest wyświetlany w następującym przykładowym kodzie.  
  
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
  
 Przykładowy kod tworzy `Record` obiekt o nazwie `record1` , a następnie wyświetla obiekt.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Następnie próbka używa <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji do `record1` strumienia pamięci.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Następnie przykład używa <xref:System.Runtime.Serialization.DataContractSerializer> do deserializacji strumienia pamięci z powrotem do nowego `Record` obiektu i wyświetla go.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Domyślnie `DataContractSerializer` kodowanie obiektów do strumienia przy użyciu tekstowej reprezentacji XML. Można jednak mieć wpływ na kodowanie kodu XML przez przekazanie w innym składniku zapisywania. Przykład tworzy binarny moduł zapisujący przez wywołanie <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> . Następnie przekazuje moduł zapisujący i obiekt rekordu do serializatora podczas wywoływania <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> . Na koniec przykład opróżnia składnik zapisywania i raporty o długości strumieni.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Po uruchomieniu przykładu zostanie wyświetlony oryginalny rekord i deserializowany rekord, po którym następuje porównanie długości kodowania tekstu i kodowania binarnego. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład, uruchom klienta z wiersza polecenia, wpisując client\bin\client.exe.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
