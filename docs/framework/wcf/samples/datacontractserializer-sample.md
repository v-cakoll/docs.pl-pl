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
# <a name="datacontractserializer-sample"></a>Przykład elementu DataContractSerializer
Przykład DataContractSerializer pokazuje <xref:System.Runtime.Serialization.DataContractSerializer>, który wykonuje ogólne usługi serializacji i deserializacji dla klas kontraktów danych. Próbka tworzy `Record` obiekt, serializuje go do strumienia pamięci i deserializes strumienia pamięci z powrotem do innego `Record` obiektu, aby zademonstrować użycie <xref:System.Runtime.Serialization.DataContractSerializer>. . Następnie próbka serializuje `Record` obiekt przy użyciu modułu zapisującego binarnego, aby zademonstrować, jak moduł zapisujący wpływa na serializację.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt danych `Record` dla jest pokazany w poniższym przykładowym kodzie.  
  
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
  
 Przykładowy kod `Record` tworzy `record1` obiekt o nazwie, a następnie wyświetla obiekt.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Następnie używa <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji `record1` w strumieniu pamięci.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Następnie w próbce <xref:System.Runtime.Serialization.DataContractSerializer> używa do deserializacji strumienia `Record` pamięci z powrotem do nowego obiektu i wyświetla go.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Domyślnie `DataContractSerializer` koduje obiekty do strumienia przy użyciu tekstowej reprezentacji XML. Można jednak wpływać na kodowanie pliku XML, przekazując w innym modułze zapisującego. Przykład tworzy moduł zapisujący <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>binarny przez wywołanie . Następnie przekazuje moduł zapisujący i obiekt rekordu do <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>serializatora, gdy wywołuje . Na koniec przykład opróżnia moduł zapisujący i raportuje długość strumieni.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Po uruchomieniu próbki wyświetlany jest oryginalny rekord i rekord deserialnizowany, po którym następuje porównanie długości kodowania tekstu z kodowaniem binarnym. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład, uruchom klienta z wiersza polecenia, wpisując polecenie client\bin\client.exe.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
