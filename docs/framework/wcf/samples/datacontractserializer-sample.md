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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17b0d3166b742aacfb935b8ab8ba4864bf1f7188
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="datacontractserializer-sample"></a>Przykład elementu DataContractSerializer
Przedstawiono przykład elementu DataContractSerializer <xref:System.Runtime.Serialization.DataContractSerializer>, który wykonuje ogólne serializacji i deserializacji usług danych klasy kontraktu. Tworzy próbki `Record` obiektu, serializuje go do strumienia pamięci i deserializuje strumienia pamięci do innego `Record` obiektu przedstawiają sposób używania <xref:System.Runtime.Serialization.DataContractSerializer>. Następnie wykonuje serializację próbki `Record` aby zademonstrować wpływ twórcę serializacji przy użyciu binarne składnika zapisywania.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Dla kontraktu danych `Record` jest wyświetlany w następujący przykładowy kod.  
  
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
  
 Przykładowy kod tworzy `Record` obiektu o nazwie `record1` następnie wyświetla obiektu.  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Następnie używa próbki <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji `record1` do strumienia pamięci.  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Następnie używa próbki <xref:System.Runtime.Serialization.DataContractSerializer> do deserializacji strumienia pamięci do nowego `Record` obiektów i wyświetla je.  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Domyślnie `DataContractSerializer` koduje obiektów w strumieniu przy użyciu tekstową reprezentację XML. Jednak możesz wywrzeć wpływ Kodowanie XML przez przekazywanie inny edytor. Przykład tworzy binarne składnika zapisywania przez wywołanie metody <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Następnie przekazuje twórcę i obiekt rekordu do serializatora gdy wywołuje <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Na koniec próbki opróżnia twórcę i raport dotyczący długość strumienia.  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Po uruchomieniu próbki rekordzie oryginalnym i rekord zdeserializowany są wyświetlane, następuje porównanie między długość kodowanie tekstu i kodowania binarnego. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykład, uruchom klienta z wiersza polecenia, wpisując client\bin\client.exe.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a>Zobacz też
