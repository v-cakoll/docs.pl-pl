---
title: Przykład elementu DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: ef1b01ff59fc32546dca8ed9c95f3a981ed408e3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553984"
---
# <a name="datacontractserializer-sample"></a>Przykład elementu DataContractSerializer
Przedstawiono przykład elementu DataContractSerializer <xref:System.Runtime.Serialization.DataContractSerializer>, który wykonuje ogólne serializacji i deserializacji usług danych klasy kontraktu. Przykładowa aplikacja tworzy `Record` obiektu, serializuje go do strumienia pamięci i deserializuje strumień pamięci, wróć do innego `Record` obiektu, aby zademonstrować użycie <xref:System.Runtime.Serialization.DataContractSerializer>. Przykład szereguje `Record` przy użyciu binarne składnika zapisywania, aby zademonstrować, jak moduł zapisujący wpływa na serializacji.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Kontraktu danych dla `Record` przedstawiono w poniższym przykładowym kodzie.  
  
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
  
 Przykładowy kod tworzy `Record` obiektu o nazwie `record1` następnie wyświetla obiekt.  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Przykład następnie używa <xref:System.Runtime.Serialization.DataContractSerializer> serializować `record1` do strumienia pamięci.  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Następnie w przykładzie użyto <xref:System.Runtime.Serialization.DataContractSerializer> deserializować strumień pamięci w nowym `Record` obiektu i wyświetla je.  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Domyślnie `DataContractSerializer` koduje obiektów do strumienia za pomocą tekstową reprezentację XML. Jednak możesz wpływać na kodowanie pliku XML, przekazując innego składnika zapisywania. Przykładowa aplikacja tworzy binarne składnika zapisywania, wywołując <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Następnie przekazuje moduł zapisujący i obiekt rekordu do serializatora przy wywoływanych przez nią <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Na koniec próbka opróżnia moduł zapisujący i raporty w zakresie długości strumieni.  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Po uruchomieniu przykładu oryginalnego rekordu i po deserializacji rekordu są wyświetlane, następuje porównanie między długość kodowania tekstu i kodowanie binarne. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykład, uruchom klienta z poziomu wiersza polecenia, wpisując client\bin\client.exe.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a>Zobacz też
