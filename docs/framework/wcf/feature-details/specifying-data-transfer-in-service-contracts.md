---
title: Określanie transferu danych w kontraktach usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: e68ca46f9d2c562491063ae66754c469dbe0898e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184425"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Określanie transferu danych w kontraktach usług
Windows Communication Foundation (WCF) można traktować jako infrastruktury obsługi wiadomości. Operacje serwisowe mogą odbierać wiadomości, przetwarzać je i wysyłać im wiadomości. Komunikaty są opisane przy użyciu kontraktów operacyjnych. Rozważmy na przykład następującą umowę.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 W tym `GetAirfare` miejscu operacja akceptuje wiadomość `fromCity` `toCity`z informacjami o i , a następnie zwraca komunikat, który zawiera numer.  
  
 W tym temacie wyjaśniono różne sposoby, w których umowa operacji może opisywać wiadomości.  
  
## <a name="describing-messages-by-using-parameters"></a>Opisywanie wiadomości przy użyciu parametrów  
 Najprostszym sposobem opisania wiadomości jest użycie listy parametrów i zwracanej wartości. W poprzednim przykładzie `fromCity` parametry `toCity` i ciąg zostały użyte do opisania komunikatu żądania, a wartość zwracana float została użyta do opisania wiadomości odpowiedzi. Jeśli sama zwracana wartość nie wystarczy do opisania wiadomości odpowiedzi, mogą być używane parametry out. Na przykład następująca `fromCity` operacja `toCity` ma i w komunikacie żądania i numer wraz z walutą w komunikacie odpowiedzi:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ponadto można użyć parametrów odwołania, aby parametr część żądania i odpowiedzi wiadomości. Parametry muszą być typów, które mogą być serializowane (konwertowane na XML). Domyślnie WCF używa składnika <xref:System.Runtime.Serialization.DataContractSerializer> o nazwie klasy do wykonywania tej konwersji. Większość typów pierwotnych (takich `string` `float`jak `int` `DateTime`, , i .) są obsługiwane. Typy zdefiniowane przez użytkownika muszą zwykle mieć kontrakt na dane. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 Od czasu `DataContractSerializer` do czasu nie jest odpowiedni do serializacji typów. WCF obsługuje alternatywny aparat serializacji, <xref:System.Xml.Serialization.XmlSerializer>, który można również użyć do serializacji parametrów. Umożliwia <xref:System.Xml.Serialization.XmlSerializer> użycie większej kontroli nad wynikowego pliku XML `XmlAttributeAttribute`przy użyciu atrybutów, takich jak . Aby przełączyć <xref:System.Xml.Serialization.XmlSerializer> się do korzystania z dla określonej <xref:System.ServiceModel.XmlSerializerFormatAttribute> operacji lub dla całej usługi, należy zastosować atrybut do operacji lub usługi. Przykład:  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 Aby uzyskać więcej informacji, zobacz [Korzystanie z klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Pamiętaj, że ręczne <xref:System.Xml.Serialization.XmlSerializer> przełączanie do jak pokazano tutaj nie jest zalecane, chyba że masz konkretne powody, aby to zrobić, jak opisano w tym temacie.  
  
 Aby wyizolować nazwy parametrów .NET od nazw `Name` umów, można użyć atrybutu <xref:System.ServiceModel.MessageParameterAttribute> i użyć właściwości, aby ustawić nazwę kontraktu. Na przykład następująca umowa operacji jest odpowiednikiem pierwszego przykładu w tym temacie.  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a>Opisywanie pustych wiadomości  
 Pusty komunikat żądania można opisać, nie mając żadnych parametrów wejściowych lub referencyjnych. Na przykład w języku C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Na przykład w języku Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Pustą wiadomość odpowiedzi można opisać, `void` mając typ zwracany i nie ma parametrów wyjściowych lub referencyjnych. Na przykład w:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Różni się to od operacji jednokierunkowej, takiej jak:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 Operacja `SetTemperatureStatus` zwraca pustą wiadomość. Zamiast tego może zwrócić błąd, jeśli występuje problem z przetwarzaniem komunikatu wejściowego. Operacja `SetLightbulbStatus` zwraca nic. Nie ma sposobu, aby poinformować o stanie usterki z tej operacji.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Opisywanie wiadomości przy użyciu kontraktów wiadomości  
 Można użyć jednego typu do reprezentowania całej wiadomości. Chociaż jest możliwe użycie umowy danych w tym celu, zalecanym sposobem, aby to zrobić, jest użycie kontraktu wiadomości — pozwala to uniknąć niepotrzebnych poziomów zawijania w wynikowym pliku XML. Ponadto kontrakty wiadomości umożliwiają sprawowanie większej kontroli nad wiadomościami wynikowymi. Na przykład można zdecydować, które informacje powinny znajdować się w treści wiadomości, a które powinny znajdować się w nagłówkach wiadomości. W poniższym przykładzie przedstawiono użycie kontraktów wiadomości.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów na wiadomości](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> klasa jest nadal używana domyślnie. Klasa <xref:System.Xml.Serialization.XmlSerializer> może być również używana z kontraktami wiadomości. Aby to zrobić, <xref:System.ServiceModel.XmlSerializerFormatAttribute> zastosuj atrybut do operacji lub umowy i użyj <xref:System.Xml.Serialization.XmlSerializer> typów zgodnych z klasą w nagłówkach wiadomości i elementów członkowskich treści.  
  
## <a name="describing-messages-by-using-streams"></a>Opisywanie wiadomości przy użyciu strumieni  
 Innym sposobem opisywania komunikatów w <xref:System.IO.Stream> operacjach jest użycie klasy lub jednej z jej klas pochodnych w umowie operacji lub jako elementu umowy wiadomości (musi być jedynym elementem członkowskim w tym przypadku). W przypadku wiadomości przychodzących `Stream`typem musi być — nie można używać klas pochodnych.  
  
 Zamiast wywoływać serializatora, WCF pobiera dane ze strumienia i umieszcza je bezpośrednio w wiadomości wychodzącej lub pobiera dane z wiadomości przychodzącej i umieszcza je bezpośrednio w strumieniu. Poniższy przykład pokazuje użycie strumieni.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nie można `Stream` łączyć i nie przesyłać strumieniowo danych w treści pojedynczej wiadomości. Użyj umowy wiadomości, aby umieścić dodatkowe dane w nagłówkach wiadomości. Poniższy przykład pokazuje niepoprawne użycie strumieni podczas definiowania umowy operacji.  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 W poniższym przykładzie przedstawiono prawidłowe użycie strumieni podczas definiowania umowy operacji.  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 Aby uzyskać więcej informacji, zobacz [Duże dane i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Używanie klasy Message  
 Aby mieć pełną kontrolę programową nad wiadomościami <xref:System.ServiceModel.Channels.Message> wysłanymi lub odebranymi, można użyć klasy bezpośrednio, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Jest to zaawansowany scenariusz, który jest szczegółowo opisany w [using message class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Opisywanie komunikatów o błędach  
 Oprócz komunikatów, które są opisane przez wartość zwracaną i parametrów wyjściowych lub referencyjnych, każda operacja, która nie jest jednokierunkowa, może zwrócić co najmniej dwa możliwe komunikaty: jego normalny komunikat odpowiedzi i komunikat o błędzie. Należy wziąć pod uwagę następującą umowę operacji.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Ta operacja może zwrócić normalny komunikat `float` zawierający numer lub komunikat o błędzie zawierający kod usterki i opis. Można to osiągnąć, rzucając <xref:System.ServiceModel.FaultException> w implementacji usługi.  
  
 Można określić dodatkowe możliwe komunikaty o błędach przy użyciu atrybutu. <xref:System.ServiceModel.FaultContractAttribute> Dodatkowe błędy muszą być serializable <xref:System.Runtime.Serialization.DataContractSerializer>przy użyciu , jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 Te dodatkowe błędy mogą być generowane <xref:System.ServiceModel.FaultException%601> przez rzutowanie odpowiedniego typu kontraktu danych. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków i usterek](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Nie można <xref:System.Xml.Serialization.XmlSerializer> użyć klasy do opisania błędów. Nie <xref:System.ServiceModel.XmlSerializerFormatAttribute> ma to wpływu na umowy o usterkę.  
  
## <a name="using-derived-types"></a>Korzystanie z typów pochodnych  
 Można użyć typu podstawowego w operacji lub umowy wiadomości, a następnie użyć typu pochodnego podczas faktycznie wywoływania operacji. W takim przypadku należy użyć <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub innego alternatywnego mechanizmu, aby umożliwić użycie typów pochodnych. Należy wziąć pod uwagę następującą operację.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Załóżmy, `Book` że `Magazine`dwa typy i , pochodzą od `LibraryItem`. Aby użyć tych `IsLibraryItemAvailable` typów w operacji, można zmienić operację w następujący sposób:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatywnie można użyć <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu, gdy <xref:System.Runtime.Serialization.DataContractSerializer> jest używany wartość domyślna, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 Można użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu podczas <xref:System.Xml.Serialization.XmlSerializer>korzystania z pliku .  
  
 Można zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybut do operacji lub do całej usługi. Akceptuje typ lub nazwę metody do wywołania, aby uzyskać listę znanych typów, <xref:System.Runtime.Serialization.KnownTypeAttribute> podobnie jak atrybut. Aby uzyskać więcej informacji, zobacz [Znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Określanie sposobu użycia i stylu  
 Opisując usługi przy użyciu języka opisu usług sieci Web (WSDL), dwa powszechnie używane style to Document and remote procedure call (RPC). W stylu Dokumentu cała treść wiadomości jest opisana przy użyciu schematu, a WSDL opisuje różne części treści wiadomości, odwołując się do elementów w tym schemacie. W stylu RPC WSDL odwołuje się do typu schematu dla każdej części wiadomości, a nie elementu. W niektórych przypadkach należy ręcznie wybrać jeden z tych stylów. Można to zrobić, stosując <xref:System.ServiceModel.DataContractFormatAttribute> atrybut i `Style` ustawiając właściwość <xref:System.Runtime.Serialization.DataContractSerializer> (gdy jest `Style` używana) <xref:System.ServiceModel.XmlSerializerFormatAttribute> lub ustawiając <xref:System.Xml.Serialization.XmlSerializer>atrybut (podczas korzystania z ).  
  
 Dodatkowo <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwie formy serializowanego XML: `Literal` i `Encoded`. `Literal`jest najczęściej akceptowanym formularzem i jest jedyną formą podpory. <xref:System.Runtime.Serialization.DataContractSerializer> `Encoded`jest starszą formą opisaną w sekcji 5 specyfikacji PROTOKOŁU SOAP i nie jest zalecana w przypadku nowych usług. Aby przełączyć `Encoded` się `Use` do trybu, ustaw właściwość atrybutu <xref:System.ServiceModel.XmlSerializerFormatAttribute> . `Encoded`  
  
 W większości przypadków nie należy zmieniać ustawień `Style` `Use` domyślnych dla i właściwości.  
  
## <a name="controlling-the-serialization-process"></a>Kontrolowanie procesu serializacji  
 Można wykonać wiele czynności, aby dostosować sposób serializacji danych.  
  
### <a name="changing-server-serialization-settings"></a>Zmiana ustawień serializacji serwera  
 Gdy wartość <xref:System.Runtime.Serialization.DataContractSerializer> domyślna jest w użyciu, można kontrolować niektóre aspekty procesu <xref:System.ServiceModel.ServiceBehaviorAttribute> serializacji w usłudze, stosując atrybut do usługi. W szczególności można użyć `MaxItemsInObjectGraph` właściwości, aby ustawić przydział, który <xref:System.Runtime.Serialization.DataContractSerializer> ogranicza maksymalną liczbę obiektów deserializes. Za pomocą `IgnoreExtensionDataObject` tej właściwości można wyłączyć funkcję usuwania wersji zaokrąglania. Aby uzyskać więcej informacji na temat przydziałów, zobacz [Zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Aby uzyskać więcej informacji na temat potknięcia zaokrąglania, zobacz [Kontrakty danych zgodne z przekazywaniem](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a>Zachowania serializacji  
 Dwa zachowania są dostępne w WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> które są automatycznie podłączone w zależności od serializatora jest używany dla określonej operacji. Ponieważ te zachowania są stosowane automatycznie, zwykle nie trzeba być świadomym ich.  
  
 Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`i `DataContractSurrogate` właściwości, które można użyć do dostosowania procesu serializacji. Pierwsze dwie właściwości mają takie samo znaczenie, jak omówiono w poprzedniej sekcji. Właściwości można `DataContractSurrogate` użyć, aby włączyć zastępcze umowy danych, które są potężnym mechanizmem dostosowywania i rozszerzania procesu serializacji. Aby uzyskać więcej informacji, zobacz [Zastępcze umowy danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Można użyć, `DataContractSerializerOperationBehavior` aby dostosować zarówno serializacji klienta i serwera. W poniższym przykładzie `MaxItemsInObjectGraph` pokazano, jak zwiększyć przydział na kliencie.  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
Poniżej znajduje się równoważny kod w usłudze, w przypadku hostowane samodzielnie:
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 W przypadku hostowanego w sieci Web `ServiceHost` należy utworzyć nową klasę pochodną i użyć fabryki hosta usług, aby ją podłączyć.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Kontrolowanie ustawień serializacji w konfiguracji  
 I mogą być kontrolowane za `dataContractSerializer` pomocą konfiguracji przy użyciu zachowania punktu końcowego lub usługi, jak pokazano w poniższym przykładzie. `IgnoreExtensionDataObject` `MaxItemsInObjectGraph`  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serializacja typu udostępnionego, zachowanie wykresu obiektów i serializatory niestandardowe  
 Serializes <xref:System.Runtime.Serialization.DataContractSerializer> przy użyciu nazw kontraktów danych, a nie nazw typów .NET. Jest to zgodne z zasadami architektury zorientowanych na usługi i pozwala na duży stopień elastyczności — typy .NET mogą się zmieniać bez wpływu na kontrakt przewodowy. W rzadkich przypadkach można serializować rzeczywiste nazwy typów .NET, wprowadzając w ten sposób ścisłe sprzężenie między klientem a serwerem, podobne do technologii komunikacji zdalnej .NET Framework. Nie jest to zalecana praktyka, z wyjątkiem rzadkich przypadków, które zwykle występują podczas migracji do WCF z .NET Framework komunikacji zdalnej. W takim przypadku należy <xref:System.Runtime.Serialization.NetDataContractSerializer> użyć klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 Zwykle <xref:System.Runtime.Serialization.DataContractSerializer> serializuje wykresy obiektów jako drzewa obiektów. Oznacza to, że jeśli ten sam obiekt jest określany więcej niż jeden raz, jest serializowany więcej niż jeden raz. Rozważmy na `PurchaseOrder` przykład wystąpienie, które ma `billTo` `shipTo`dwa pola typu Adres wywoływany i . Jeśli oba pola są ustawione na to samo wystąpienie Address, istnieją dwa identyczne wystąpienia adresu po serializacji i deserializacji. Odbywa się to, ponieważ nie istnieje standardowy interoperacyjny sposób reprezentowania wykresów obiektów w formacie <xref:System.Xml.Serialization.XmlSerializer>XML (z wyjątkiem starszego standardu zakodowanego w formacie SOAP dostępnego w , jak opisano w poprzedniej sekcji na `Style` i `Use`). Serializowanie wykresów obiektów jako drzew ma pewne wady, na przykład wykresy z odwołaniami cyklicznymi nie mogą być serializowane. Od czasu do czasu konieczne jest przełączenie się do serializacji wykresu obiektu true, nawet jeśli nie jest interoperacyjne. Można to zrobić za <xref:System.Runtime.Serialization.DataContractSerializer> pomocą skonstruowane z parametrem ustawionym `preserveObjectReferences` na `true`.  
  
 Od czasu do czasu wbudowane serializatory nie są wystarczające dla scenariusza. W większości przypadków można nadal <xref:System.Runtime.Serialization.XmlObjectSerializer> używać abstrakcji, <xref:System.Runtime.Serialization.NetDataContractSerializer> z której zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i pochodne.  
  
 Poprzednie trzy przypadki (.NET zachowanie typu, zachowanie wykresu obiektu i całkowicie niestandardowe `XmlObjectSerializer`serializacji) wszystkie wymagają niestandardowego serializatora być podłączone. W tym celu wykonaj następujące czynności:  
  
1. Napisz własne zachowanie wynikające <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>z .  
  
2. Zastąp `CreateSerializer` dwie metody zwracania własnego <xref:System.Runtime.Serialization.NetDataContractSerializer>serializatora <xref:System.Runtime.Serialization.DataContractSerializer> (albo , z `preserveObjectReferences` zestawem do `true`, lub własne niestandardowe). <xref:System.Runtime.Serialization.XmlObjectSerializer>  
  
3. Przed otwarciem hosta usługi lub utworzeniem <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> kanału klienta usuń istniejące zachowanie i podłącz niestandardową klasę pochodną utworzoną w poprzednich krokach.  
  
 Aby uzyskać więcej informacji na temat zaawansowanych koncepcji serializacji, zobacz [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Zobacz też

- [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Instrukcje: włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
