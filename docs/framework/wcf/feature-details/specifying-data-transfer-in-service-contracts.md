---
title: Określanie transferu danych w kontraktach usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 7423a44f7779c8e4ef75fc68e33eeb4ac48a660a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508503"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Określanie transferu danych w kontraktach usług
Windows Communication Foundation (WCF) mogą być uważane za infrastruktury obsługi wiadomości. Operacje usługi można odbierać wiadomości, ich przetworzyć i wysyłanie do nich wiadomości. Komunikaty są opisane przy użyciu kontrakty operacji. Na przykład należy wziąć pod uwagę następujące kontraktu.  
  
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
  
 W tym miejscu `GetAirfare` operacji akceptuje komunikat z informacjami o `fromCity` i `toCity`, a następnie zwraca komunikat, który zawiera liczbę.  
  
 W tym temacie opisano różne sposoby, w których kontrakt operacji można opisać wiadomości.  
  
## <a name="describing-messages-by-using-parameters"></a>Opisujące wiadomości przy użyciu parametrów  
 Najprostszym sposobem, aby opisać wiadomość jest użycie listy parametrów i zwracanych wartości. W powyższym przykładzie `fromCity` i `toCity` parametrów ciągu były używane do opisywania komunikat żądania, a wartością zwracaną typu float zostało użyte do opisu komunikatu odpowiedzi. Jeśli tylko wartości zwracanej nie jest wystarczająca do opisywania komunikat odpowiedzi, parametrów out może być używany. Na przykład następująca operacja ma `fromCity` i `toCity` komunikatu żądania i numer wraz z waluty w jego komunikat odpowiedzi:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ponadto można używać parametrów odwołania do parametru część zarówno żądanie, jak i komunikatu odpowiedzi. Parametry muszą być typów, które można serializować (przekonwertowane na format XML). Domyślnie WCF używa składnik o nazwie <xref:System.Runtime.Serialization.DataContractSerializer> klasy do wykonania konwersji. Typy pierwotne najbardziej (takich jak `int`, `string`, `float`, i `DateTime`.) są obsługiwane. Typy definiowane przez użytkownika musi mieć zwykle kontraktu danych. Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 Czasami `DataContractSerializer` nie jest odpowiednia do serializacji typów sieci. WCF obsługuje mechanizm alternatywny serializacji, <xref:System.Xml.Serialization.XmlSerializer>, który można serializować parametrów. <xref:System.Xml.Serialization.XmlSerializer> Umożliwia użycie większą kontrolę nad wynikowego pliku XML przy użyciu atrybutów, takich jak `XmlAttributeAttribute`. Aby przełączyć się do przy użyciu <xref:System.Xml.Serialization.XmlSerializer> mają zastosowanie dla określonej operacji lub dla całej usługi <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu w celu wykonania operacji lub usługi. Na przykład:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Należy pamiętać, że ręczne przełączanie do <xref:System.Xml.Serialization.XmlSerializer> opisane w tym miejscu nie jest zalecane, chyba że masz właściwe przyczyny robić, tak jak szczegółowe, w tym temacie.  
  
 Aby wyizolować .NET nazwy parametru od nazw kontraktu, można użyć <xref:System.ServiceModel.MessageParameterAttribute> atrybutu, a następnie użyj `Name` właściwości można ustawić nazwy kontraktu. Na przykład następujące kontrakt operacji jest odpowiednikiem pierwszym przykładzie w tym temacie.  
  
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
 Komunikat żądania pusty można opisać za pomocą o bez parametrów wejściowych lub odwołanie. Na przykład w języku C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Na przykład w języku Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Komunikat odpowiedzi pusty można opisać za pomocą o `void` zwracany typ i bez parametrów wyjściowych lub odwołanie. Na przykład w:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Różni się to od operacji jednokierunkowych, takich jak:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus` Operacja zwraca komunikat puste. Go mogą zwracać błąd zamiast tego przypadku problem podczas przetwarzania komunikatu wejściowego. `SetLightbulbStatus` Operacji nie zwraca żadnego. Nie istnieje sposób do komunikowania się warunek błędu z tej operacji.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Opisujące wiadomości za pomocą kontraktów komunikatu  
 Można użyć jednego typu do reprezentowania cały komunikat. Jest możliwe użycie kontraktu danych do tego celu, w tym zalecaną metodą jest użycie kontraktu komunikatu — dzięki temu można uniknąć niepotrzebnych poziomów zawijania wynikowe dane XML. Ponadto kontraktów komunikatu umożliwiają większej kontroli nad wynikowe wiadomości. Na przykład można zdecydować, informacje powinna być w treści wiadomości i powinny być w nagłówkach wiadomości. Poniższy przykład przedstawia użycie kontraktów komunikatu.  
  
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
  
 W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> klasy jest wciąż używany domyślnie. <xref:System.Xml.Serialization.XmlSerializer> Klasa może być używana również z kontraktów komunikatu. Aby to zrobić, należy zastosować <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu w celu wykonania operacji lub kontrakt i używanie typów zgodne z <xref:System.Xml.Serialization.XmlSerializer> klasy w nagłówkach wiadomości i członków treści.  
  
## <a name="describing-messages-by-using-streams"></a>Opisujące wiadomości przy użyciu strumieni  
 Innym sposobem opisują komunikaty w operacji jest użycie <xref:System.IO.Stream> klasy lub jednej z jej klas pochodnych w kontrakt operacji lub jako członek treści kontraktu komunikatu (musi być jedynym członkiem w takim przypadku). Dla komunikatów przychodzących, typ musi być `Stream`— nie można używać klas pochodnych.  
  
 Zamiast wywoływania serializator, WCF pobiera dane ze strumienia i umieszcza je bezpośrednio do wiadomości wychodzącej lub pobiera dane z komunikatu przychodzącego i umieszcza je bezpośrednio do strumienia. Poniższy przykład przedstawia korzystanie ze strumieni.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nie można łączyć `Stream` i danych z systemem innym niż strumienia w treści wiadomości. Użyj kontraktu komunikatu, aby umieścić dodatkowe dane w nagłówkach wiadomości. W poniższym przykładzie przedstawiono nieprawidłowe użycie strumieni podczas definiowania kontrakt operacji.  
  
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
  
 Poniższy przykład przedstawia odpowiednie użycie strumieni podczas definiowania kontrakt operacji.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [duże ilości danych i przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Używanie klasy Message  
 Aby mieć pełną kontrolę programowy za pośrednictwem wiadomości wysyłane lub odbierane, można użyć <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio, jak pokazano w poniższym przykładzie kodzie.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Jest to bardziej zaawansowany scenariusz, który opisano szczegółowo w [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Opisujące komunikatów "Fault"  
 Oprócz wiadomości, które są opisane w zwracanej wartości i parametrów wyjściowych lub odwołanie, żadnej operacji, która nie jest jednokierunkowa można zwrócić co najmniej dwa komunikaty możliwe: komunikatu odpowiedzi normalne i komunikat o błędzie. Należy wziąć pod uwagę następujące kontrakt operacji.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Ta operacja albo może zwracać normalne komunikat, który zawiera `float` numer lub komunikat o błędzie, który zawiera kod błędu i opis. Można to zrobić przez zgłaszanie <xref:System.ServiceModel.FaultException> w implementacji usługi.  
  
 Można określić dodatkowe możliwych błędów wiadomości przy użyciu <xref:System.ServiceModel.FaultContractAttribute> atrybutu. Dodatkowe błędy musi być możliwy do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładzie kodzie.  
  
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
  
 Nie można użyć <xref:System.Xml.Serialization.XmlSerializer> klasy do opisywania błędów. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Nie ma wpływu na kontrakty błędów.  
  
## <a name="using-derived-types"></a>Przy użyciu typów pochodnych  
 Można użyć typu podstawowego w operacji lub kontraktu komunikatu, a następnie użyj typu pochodnego podczas faktycznie wywoływania operacji. W takim przypadku należy użyć jednego <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub niektóre alternatywny mechanizm zezwala na używanie typów pochodnych. Należy rozważyć następujące działania.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Załóżmy, że dwa typy, `Book` i `Magazine`, pochodzi z `LibraryItem`. Używanie tych typów w `IsLibraryItemAvailable` operacji, można zmienić operację w następujący sposób:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatywnie można użyć <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu, gdy domyślny <xref:System.Runtime.Serialization.DataContractSerializer> jest w użyciu, jak pokazano w poniższym przykładzie kodzie.  
  
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
  
 Można użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Możesz zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu operacji lub całej usługi. Przyjmuje typ albo nazwa metody do wywołania w celu uzyskania listy znanych typów, podobnie jak <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Określanie Use i Style  
 W opisie usług za pomocą sieci Web Services Description Language (WSDL), dwa najczęściej używane style są dokument i zdalnego wywołania procedury (RPC). W stylu dokumentu opisano treści cały komunikat przy użyciu schematu i WSDL opisano różne części treści wiadomości, odwołując się do elementów w ramach tego schematu. W stylu wywołania RPC WSDL odwołuje się do typu schematu dla każdej części komunikatu zamiast elementu. W niektórych przypadkach należy ręcznie wybrać jeden z tych stylów. Można to zrobić przez zastosowanie <xref:System.ServiceModel.DataContractFormatAttribute> atrybut i ustawienie `Style` właściwości (przy <xref:System.Runtime.Serialization.DataContractSerializer> jest używany), lub przez ustawienie `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu (przy użyciu <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Ponadto <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwa rodzaje serializacji XML: `Literal` i `Encoded`. `Literal` jest najczęściej zaakceptowane formularza i jest jedyną <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje. `Encoded` jest formą starszych opisane w sekcji 5 specyfikacji protokołu SOAP, a nie jest zalecane w przypadku nowych usług. Aby przełączyć się do `Encoded` tryb, `Use` właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu `Encoded`.  
  
 W większości przypadków, nie należy zmieniać ustawienia domyślne dla `Style` i `Use` właściwości.  
  
## <a name="controlling-the-serialization-process"></a>Kontrolowanie procesu serializacji  
 Można zrobić na kilka rzeczy, które można dostosować sposób danych jest serializowany.  
  
### <a name="changing-server-serialization-settings"></a>Zmiana ustawień serializacji serwera  
 Gdy domyślne <xref:System.Runtime.Serialization.DataContractSerializer> jest używana, można kontrolować niektóre aspekty procesu serializacji w usłudze, stosując <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu z usługą. W szczególności mogą używać `MaxItemsInObjectGraph` właściwości można ustawić limit przydziału, która ogranicza maksymalną liczbę obiektów <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje. Można użyć `IgnoreExtensionDataObject` właściwości, aby wyłączyć funkcji przechowywania wersji dwustronną komunikację. Aby uzyskać więcej informacji na temat przydziałów, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Aby uzyskać więcej informacji na temat dwustronną komunikację, zobacz [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 Dwa zachowania są dostępne w programie WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> który automatycznie są podłączone w zależności od którego serializator jest używana dla określonej operacji. Ponieważ te zachowania są automatycznie stosowane, zwykle nie trzeba się z nimi zapoznać.  
  
 Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, i `DataContractSurrogate` właściwości, których można użyć do dostosowania procesu serializacji. Pierwsze dwie właściwości mają takie samo znaczenie, zgodnie z opisem w poprzedniej sekcji. Można użyć `DataContractSurrogate` właściwości, aby włączyć surogaty kontraktu danych, które są zaawansowany mechanizm dostosowywanie i rozszerzanie procesu serializacji. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Można użyć `DataContractSerializerOperationBehavior` dostosować serializacji klienta i serwera. Poniższy przykład przedstawia sposób zwiększenia `MaxItemsInObjectGraph` przydziału na kliencie.  
  
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
  
 Poniżej znajduje się kod równoważne usługi, w przypadku hostowania samoobsługowego.  
  
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
  
 W przypadku hostowanych w sieci Web, należy utworzyć nowy `ServiceHost` klasy i dołączyć go przy użyciu fabryki hostów usług.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Kontrolowanie serializacji ustawień konfiguracji  
 `MaxItemsInObjectGraph` i `IgnoreExtensionDataObject` można sterować za pomocą konfiguracji przy użyciu `dataContractSerializer` zachowanie punktu końcowego lub usługi, jak pokazano w poniższym przykładzie.  
  
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
            <endpoint address=http://example.com/myservice  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Wspólnego typu serializacji, zachowywania wykres obiektu i serializatorów niestandardowych  
 <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje przy użyciu nazwy kontraktu danych, a nie nazwy typów .NET. To jest zgodna z zorientowane na usługę architektura rozwiązań i umożliwia precyzyjną elastyczność — typów .NET, można zmienić bez wpływu na kontraktu danych przesyłanych w sieci. W rzadkich przypadkach można serializować rzeczywistej nazwy typów .NET, co wprowadzenie ścisłej sprzężenia między klientem i serwerem, podobnie jak technologię zdalnych .NET Framework. To nie jest zalecanym rozwiązaniem, z wyjątkiem w rzadkich przypadkach, zwykle występujących podczas migracji do programu WCF z usługi zdalne środowiska .NET Framework. W takim przypadku należy użyć <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Zwykle serializuje wykresów obiektów jako drzewa obiektów. Oznacza to jeżeli ten sam obiekt jest określona więcej niż raz, jego jest serializowane więcej niż raz. Rozważmy na przykład `PurchaseOrder` wystąpienia, która ma dwa pola typu o nazwie adresu `billTo` i `shipTo`. Jeśli oba pola są ustawione w tym samym wystąpieniu adres, istnieją dwa identyczne wystąpienia adres po serializacji i deserializacji. Odbywa się, ponieważ nie istnieje standardowy sposób interoperacyjne do reprezentowania wykresów obiektów w pliku XML (z wyjątkiem dostępne w starszej wersji standard SOAP zakodowane <xref:System.Xml.Serialization.XmlSerializer>, zgodnie z opisem w poprzedniej sekcji na `Style` i `Use`). Serializacja wykresów obiektów jako drzewa ma niektóre wady, na przykład nie można zserializować wykresów z odwołań cyklicznych. Czasami jest niezbędne przełączyć się do serializacji wykres obiektu wartość true, mimo że nie jest współdziałanie. Można to zrobić za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> skonstruowany przy `preserveObjectReferences` ustawiono parametr `true`.  
  
 Czasami wbudowanych serializatorów nie są wystarczająco dla danego scenariusza. W większości przypadków można nadal używać <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakcji, z których obie <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodzi.  
  
 Poprzednie trzech przypadkach (zachowania typu .NET, zachowywania wykres obiektu i całkowicie niestandardowych `XmlObjectSerializer`— na podstawie serializacji) wymaga niestandardowy serializator są podłączone. W tym celu wykonaj następujące czynności:  
  
1.  Pisanie własnych zachowanie wynikające z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2.  Zastąpienie dwa `CreateSerializer` metod do zwrócenia własny serializator (albo <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> z `preserveObjectReferences` ustawioną `true`, lub własne niestandardowe <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3.  Przed otwarciem hosta usługi lub tworzenie kanału klienta, Usuń istniejące <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zachowanie i wtyczki w klasie pochodnej niestandardowe utworzone w poprzednich krokach.  
  
 Aby uzyskać więcej informacji o pojęciach serializacji zaawansowanych, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [Instrukcje: włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
