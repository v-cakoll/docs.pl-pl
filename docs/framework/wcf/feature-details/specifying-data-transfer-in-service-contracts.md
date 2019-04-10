---
title: Określanie transferu danych w kontraktach usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 88bdfe6e659e6e83365b3d17c9067581f209d154
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331523"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Określanie transferu danych w kontraktach usług
Windows Communication Foundation (WCF) mogą być uważane za to infrastruktura obsługi komunikatów. Operacje usługi można odbierać komunikaty, przetwarzać je i wysyłania im komunikatów. Komunikaty są opisane za pomocą kontrakty operacji. Na przykład należy wziąć pod uwagę następujące umowy.  
  
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
  
 W tym miejscu `GetAirfare` operacji akceptuje komunikat z informacjami o `fromCity` i `toCity`, a następnie zwraca komunikat, który zawiera numer.  
  
 W tym temacie opisano różne sposoby, w których kontrakt operacji można opisać wiadomości.  
  
## <a name="describing-messages-by-using-parameters"></a>Opisujące wiadomości przy użyciu parametrów  
 Najprostszym sposobem opisują wiadomość jest listą parametrów i wartości zwracanej. W powyższym przykładzie `fromCity` i `toCity` parametry były używane do opisywania komunikat żądania, a wartość zwracaną float został użyty do opisania komunikatu odpowiedzi. Jeśli samodzielnie wartość zwracana nie jest wystarczająco dużo, aby opisać komunikat odpowiedzi, parametry wyjściowe mogą być używane. Na przykład następująca operacja ma `fromCity` i `toCity` w jego komunikat żądania oraz numer wraz z waluty w jego komunikat odpowiedzi:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ponadto można używać parametrów odwołania do parametru częścią zarówno żądanie, jak i komunikatu odpowiedzi. Parametry muszą być typów, które można wykonywać serializację (przekonwertować na format XML). Domyślnie program WCF używa składnik o nazwie <xref:System.Runtime.Serialization.DataContractSerializer> klasy, aby wykonać tę konwersję. Typy pierwotne najbardziej (takie jak `int`, `string`, `float`, i `DateTime`.) są obsługiwane. Typy zdefiniowane przez użytkownika musi mieć zwykle kontraktu danych. Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 Od czasu do czasu `DataContractSerializer` nie jest odpowiednia do serializacji typów. Usługi WCF obsługuje mechanizm serializacji alternatywne, <xref:System.Xml.Serialization.XmlSerializer>, który umożliwia także serializować parametrów. <xref:System.Xml.Serialization.XmlSerializer> Umożliwia większą kontrolę nad wynikowy kod XML przy użyciu atrybutów, takich jak `XmlAttributeAttribute`. Aby przełączyć się do korzystania z <xref:System.Xml.Serialization.XmlSerializer> dla określonej operacji lub dla całej usługi naliczone <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu do operacji lub usługi. Na przykład:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Należy pamiętać, że ręczne przełączanie do <xref:System.Xml.Serialization.XmlSerializer> jak pokazano w tym miejscu nie jest zalecane, chyba że masz powody, aby zrobić tak jak wyjaśniono w tym temacie.  
  
 Aby wyizolować .NET nazwy parametru od nazw kontraktu, można użyć <xref:System.ServiceModel.MessageParameterAttribute> atrybutu, a następnie użyj `Name` właściwość można ustawić nazwy kontraktu. Na przykład następujące kontrakt operacji jest równoważne z pierwszego przykładu w tym temacie.  
  
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
  
## <a name="describing-empty-messages"></a>Opisujące pusty wiadomości  
 Komunikat żądania pustą można opisać za pomocą o bez parametrów danych wejściowych lub odwołania. Na przykład w C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Na przykład w języku VB:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Komunikat odpowiedzi pusty można opisać za pomocą o `void` zwracać typ i bez parametrów danych wyjściowych lub odwołania. Na przykład w:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 To różni się od operacji jednokierunkowych, takich jak:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus` Operacja zwraca pusty komunikat. Jego może zwracać błędów zamiast Jeśli występuje problem podczas przetwarzania komunikatu wejściowego. `SetLightbulbStatus` Operacji nie zwraca żadnego. Nie ma możliwości do komunikowania się warunek błędu z tej operacji.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Opisujące komunikatów za pomocą kontraktów komunikatu  
 Można użyć jednego typu do reprezentowania cały komunikat. Chociaż jest możliwe użycie kontraktu danych, w tym celu, zalecanym sposobem na to jest użycie kontraktu komunikatu — pozwala to uniknąć niepotrzebnych poziomy zawijania wynikowego pliku XML. Kontrakty komunikatów umożliwiają ponadto większa kontrola nad wynikowe wiadomości. Na przykład można zdecydować, informacje powinien znajdować się w treści komunikatu i powinien być w nagłówkach wiadomości. Używanie kontraktów komunikatu można znaleźć w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> klasy jest nadal używana domyślnie. <xref:System.Xml.Serialization.XmlSerializer> Klasy można również za pomocą kontraktów komunikatu. Aby to zrobić, należy zastosować <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu do operacji lub umowy i używanie typów zgodnych z <xref:System.Xml.Serialization.XmlSerializer> klasy w nagłówki komunikatów i elementów członkowskich jednostki.  
  
## <a name="describing-messages-by-using-streams"></a>Opisujące komunikatów za pomocą strumieni  
 Opisują komunikaty w operacjach na innym sposobem jest użycie <xref:System.IO.Stream> klasy lub jednej z jej klas pochodnych w kontrakt operacji lub jako członek treści kontraktu komunikatu (musi mieć wartość tylko element członkowski w tym przypadku). Dla wiadomości przychodzących, musi być typu `Stream`— nie można użyć klas pochodnych.  
  
 Zamiast wywoływania serializator, WCF pobiera dane ze strumienia i umieszcza go bezpośrednio do wysyłanej wiadomości lub pobiera dane z wiadomości przychodzących i umieszcza go bezpośrednio do strumienia. Poniższy przykład pokazuje użycie strumieni.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nie można łączyć `Stream` i Transmituj — w treści pojedynczym komunikacie. Użyj kontraktu komunikatu, aby umieścić dodatkowe dane w nagłówkach wiadomości. Poniższy kod przedstawia nieprawidłowe użycie strumieni podczas definiowania kontrakt operacji.  
  
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
  
 Poniższy przykład pokazuje poprawne użycie strumieni podczas definiowania kontrakt operacji.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Używanie klasy Message  
 Aby mieć pełną kontrolę programowy za pośrednictwem wiadomości wysyłane lub odbierane, można użyć <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Jest to zaawansowany scenariusz, opisana szczegółowo w temacie [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Opisujące komunikaty o błędach  
 Oprócz wiadomości, które są opisane przez wartość zwracaną i parametry danych wyjściowych lub odwołania, każdej operacji, która nie jest jednokierunkowa może zwrócić co najmniej dwa możliwe komunikaty: komunikat odpowiedzi normalne i komunikatu o błędzie. Należy wziąć pod uwagę następujące kontrakt operacji.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Ta operacja albo może zwracać normalny komunikat dotyczący, który zawiera `float` numer lub komunikat o błędzie, który zawiera kod błędu i opis. Można to zrobić, zwracając <xref:System.ServiceModel.FaultException> w danej implementacji usługi.  
  
 Komunikaty dodatkowych możliwych błędów można określić za pomocą <xref:System.ServiceModel.FaultContractAttribute> atrybutu. Dodatkowe błędy musi być możliwy do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Te dodatkowe błędy mogą być generowane przez zgłaszanie <xref:System.ServiceModel.FaultException%601> typu kontraktu danych. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Nie można użyć <xref:System.Xml.Serialization.XmlSerializer> klasę do opisania błędów. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Nie ma wpływu na kontraktów błędów.  
  
## <a name="using-derived-types"></a>Przy użyciu typów pochodnych  
 Można użyć typu podstawowego w operacji lub kontraktu komunikatu, a następnie użyj typu pochodnego, podczas wywoływania faktycznie wykonać operację. W takim przypadku należy użyć <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub niektóre alternatywny mechanizm umożliwiający korzystanie z typów pochodnych. Należy wziąć pod uwagę następujące działania.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Przyjęto założenie, że dwa typy `Book` i `Magazine`, pochodzi od `LibraryItem`. Używanie tych typów w `IsLibraryItemAvailable` operacji, można zmienić operacji w następujący sposób:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatywnie, można użyć <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu, gdy domyślny <xref:System.Runtime.Serialization.DataContractSerializer> jest w użyciu, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Możesz użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Można zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutów, operacji lub całą usługę. Przyjmuje typ albo nazwa metody do wywołania w celu uzyskania listy znanych typów, podobnie jak <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Określanie Use i Style  
 W opisie usług za pomocą sieci Web Services Description Language (WSDL), dwa najczęściej używane style są dokument i zdalnego wywołania procedury (RPC). W stylu dokumentu opisano treści cały komunikat przy użyciu schematu i WSDL w tym artykule opisano różne części treści wiadomości, odwołując się do elementów w tym schemacie. W stylu RPC WSDL odwołuje się do typu schematu dla każdej części komunikatu zamiast elementu. W niektórych przypadkach trzeba ręcznie wybrać jeden z tych stylów. Można to robić przez zastosowanie <xref:System.ServiceModel.DataContractFormatAttribute> atrybutów i ustawienie `Style` właściwości (po <xref:System.Runtime.Serialization.DataContractSerializer> jest używany), lub poprzez skonfigurowanie `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu (korzystając z <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Ponadto <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwa rodzaje serializacji XML: `Literal` i `Encoded`. `Literal` to najbardziej powszechnie akceptowane formularza i jest tylko formularz <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje. `Encoded` jest formą starszych opisane w sekcji 5 specyfikacji protokołu SOAP, a nie jest zalecane w przypadku nowych usług. Aby przełączyć się do `Encoded` ustawiony tryb, `Use` właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu `Encoded`.  
  
 W większości przypadków nie należy zmieniać domyślne ustawienia dla `Style` i `Use` właściwości.  
  
## <a name="controlling-the-serialization-process"></a>Sterowanie procesem serializacji  
 Można zrobić kilka rzeczy, aby dostosować sposób, w jaki dane jest serializowana.  
  
### <a name="changing-server-serialization-settings"></a>Zmienianie ustawień serializacji serwera  
 Gdy domyślne <xref:System.Runtime.Serialization.DataContractSerializer> jest używany, można kontrolować niektóre aspekty procesu serializacji w usłudze, stosując <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu w usłudze. W szczególności można użyć `MaxItemsInObjectGraph` właściwość umożliwiająca ustawienie limitu przydziału, która ogranicza maksymalną liczbę obiektów <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje. Możesz użyć `IgnoreExtensionDataObject` właściwości, aby wyłączyć funkcji przechowywania wersji Pełna zgodnooć wersji. Aby uzyskać więcej informacji na temat limitów przydziału, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Aby uzyskać więcej informacji na temat Pełna zgodnooć wersji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 Dwa zachowania są dostępne w programie WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , automatycznie są podłączone w zależności od którego serializator jest używany dla określonej operacji. Ponieważ te zachowania są stosowane automatycznie, zwykle nie trzeba się z nimi zapoznać.  
  
 Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, i `DataContractSurrogate` właściwości, które umożliwiają dostosowanie procesu serializacji. Pierwsze dwie właściwości mają takie samo znaczenie, zgodnie z opisem w poprzedniej sekcji. Możesz użyć `DataContractSurrogate` właściwością pozwalającą włączyć surogaty kontraktu danych, które zaawansowany mechanizm dostosowywanie i rozszerzanie procesem serializacji. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Możesz użyć `DataContractSerializerOperationBehavior` dostosować serializacji klienta i serwera. Poniższy przykład pokazuje, jak zwiększyć `MaxItemsInObjectGraph` limitu przydziału na komputerze klienckim.  
  
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
  
 Poniżej przedstawiono równoważny kod w tym przypadku samodzielnie hostowanej usłudze.  
  
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
  
 W przypadku hostowanych w sieci Web, należy utworzyć nowy `ServiceHost` klasy pochodnej, a następnie dołączyć go za pomocą fabryki hostów usług.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Kontrolowanie serializacji ustawień konfiguracji  
 `MaxItemsInObjectGraph` i `IgnoreExtensionDataObject` mogą być kontrolowane za pośrednictwem konfiguracji za pomocą `dataContractSerializer` zachowanie punktu końcowego lub usługi, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Udostępniony serializacja typów, zachowywania wykresu obiektu i serializatorów niestandardowe  
 <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje przy użyciu nazwy kontraktów danych i nie nazwy typów .NET. To jest spójna z założenia architektury zorientowanej na usługi i umożliwia precyzyjną elastyczność — typy .NET można zmienić bez wpływu na kontrakt o komunikacji sieciowej. W rzadkich przypadkach można serializować rzeczywiste nazwy typu .NET, a tym samym Przedstawiamy ścisłego sprzężenia między klientem a serwerem, podobne do technologii wywołaniem funkcji zdalnych .NET Framework. To nie jest zalecana praktyka, z wyjątkiem w rzadkich przypadkach, zwykle występujących podczas migracji do programu WCF z wywołaniem funkcji zdalnych .NET Framework. W takim przypadku należy użyć <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Zwykle serializuje wykresów obiektów jako drzewa obiektów. Oznacza to jeżeli ten sam obiekt jest określona więcej niż jeden raz, jest serializowana więcej niż jeden raz. Na przykład, rozważmy `PurchaseOrder` wystąpienia, która ma dwa pola typu adres o nazwie `billTo` i `shipTo`. Jeśli oba pola są ustawione na tym samym wystąpieniu adres, istnieją dwa identyczne wystąpienia adres po serializacji i deserializacji. Odbywa się, ponieważ nie istnieje żadne standardowy sposób interoperacyjny do reprezentowania wykresów obiektów w formacie XML (z wyjątkiem dostępne w starszej wersji standard protokołu SOAP zakodowane <xref:System.Xml.Serialization.XmlSerializer>, zgodnie z opisem w poprzedniej sekcji na `Style` i `Use`). Serializowanie wykresów obiektów jako drzewa ma pewne wady, na przykład wykresów z odwołania cykliczne nie może być serializowany. Od czasu do czasu jest niezbędne przełączyć się do serializacji grafu obiektów wartość true, mimo że nie ma międzyoperacyjnych. Można to zrobić za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> skonstruowany przy użyciu `preserveObjectReferences` parametr `true`.  
  
 Od czasu do czasu wbudowane serializatory nie są wystarczające dla danego scenariusza. W większości przypadków można nadal używać <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakcji, z których obie <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodnych.  
  
 Poprzednie trzy przypadki (zachowywanie typu .NET, konserwowania wykresu obiektu i całkowicie niestandardowe `XmlObjectSerializer`— na podstawie serializacji) wymaga niestandardowy serializator są podłączone. W tym celu wykonaj następujące czynności:  
  
1. Napisać własne zachowanie wynikające z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2. Zastąp dwa `CreateSerializer` metody zwracają własne serializatora (albo <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> z `preserveObjectReferences` równa `true`, lub własne niestandardowe <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3. Przed otwarciem hosta usługi lub tworzenia kanału klienta, Usuń istniejące <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zachowanie i wtyczki niestandardowe klasy pochodnej, który został utworzony w poprzednich krokach.  
  
 Aby uzyskać więcej informacji o pojęciach dotyczących zaawansowanych serializacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Zobacz także

- [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Instrukcje: włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
