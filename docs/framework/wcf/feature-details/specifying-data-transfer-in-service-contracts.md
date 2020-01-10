---
title: Określanie transferu danych w kontraktach usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 50f2444764ddb212513550ff0a62fcfecab2c45a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347997"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Określanie transferu danych w kontraktach usług
Windows Communication Foundation (WCF) można traktować jako infrastrukturę obsługi komunikatów. Operacje usługi mogą odbierać komunikaty, przetwarzać je i wysyłać do nich komunikaty. Komunikaty są opisane przy użyciu kontraktów operacji. Rozważmy na przykład następujący kontrakt.  
  
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
  
 W tym miejscu operacja `GetAirfare` akceptuje komunikat z informacjami dotyczącymi `fromCity` i `toCity`, a następnie zwraca komunikat zawierający liczbę.  
  
 W tym temacie wyjaśniono różne sposoby opisywania komunikatów przez kontrakt operacji.  
  
## <a name="describing-messages-by-using-parameters"></a>Opisywanie komunikatów przy użyciu parametrów  
 Najprostszym sposobem opisywania wiadomości jest użycie listy parametrów i wartości zwracanej. W poprzednim przykładzie parametry `fromCity` i `toCity` ciąg zostały użyte do opisania komunikatu żądania, a wartość zwracana zmiennoprzecinkowa została użyta do opisania komunikatu odpowiedzi. Jeśli wartość zwracana jest zbyt mała, aby opisać komunikat odpowiedzi, można użyć parametrów out. Na przykład następująca operacja ma `fromCity` i `toCity` w jego komunikacie żądania oraz liczbę wraz z walutą w swojej wiadomości odpowiedzi:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ponadto możesz użyć parametrów odwołania, aby utworzyć część parametru zarówno żądania, jak i odpowiedzi. Parametry muszą być typami, które mogą być serializowane (konwertowane na XML). Domyślnie WCF używa składnika o nazwie <xref:System.Runtime.Serialization.DataContractSerializer> Class do wykonania tej konwersji. Obsługiwane są większość typów pierwotnych (takich jak `int`, `string`, `float`i `DateTime`). Typy zdefiniowane przez użytkownika muszą zwykle mieć kontrakt danych. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 Czasami `DataContractSerializer` nie jest wystarczający do serializacji typów. Usługa WCF obsługuje alternatywny aparat serializacji, <xref:System.Xml.Serialization.XmlSerializer>, którego można również użyć do serializacji parametrów. <xref:System.Xml.Serialization.XmlSerializer> pozwala na używanie większej kontroli nad wynikowym kodem XML przy użyciu atrybutów takich jak `XmlAttributeAttribute`. Aby przełączyć się do korzystania z <xref:System.Xml.Serialization.XmlSerializer> dla określonej operacji lub dla całej usługi, zastosuj atrybut <xref:System.ServiceModel.XmlSerializerFormatAttribute> do operacji lub usługi. Na przykład:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Należy pamiętać, że ręczne przełączenie do <xref:System.Xml.Serialization.XmlSerializer>, jak pokazano w tym miejscu, nie jest zalecane, chyba że masz określone przyczyny, zgodnie z opisem w tym temacie.  
  
 Aby izolować nazwy parametrów .NET z nazw kontraktów, można użyć atrybutu <xref:System.ServiceModel.MessageParameterAttribute> i użyć właściwości `Name` do ustawienia nazwy kontraktu. Na przykład następujący kontrakt operacji jest odpowiednikiem pierwszego przykładu w tym temacie.  
  
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
 Pusty komunikat żądania może być opisany przez brak parametrów wejściowych lub referencyjnych. Na przykład w C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Na przykład w Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Pusty komunikat odpowiedzi można opisać poprzez posiadanie `void` zwracanego typu i brak parametrów wyjściowych lub referencyjnych. Na przykład w:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Różni się to od operacji jednokierunkowej, na przykład:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 Operacja `SetTemperatureStatus` zwraca pusty komunikat. Może zwrócić błąd zamiast tego, jeśli wystąpił problem podczas przetwarzania komunikatu wejściowego. Operacja `SetLightbulbStatus` nie zwraca żadnej wartości. Nie ma możliwości komunikacji z warunkiem błędu z tej operacji.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Opisywanie komunikatów przy użyciu kontraktów komunikatów  
 Możesz chcieć użyć jednego typu do reprezentowania całej wiadomości. Chociaż istnieje możliwość użycia w tym celu kontraktu danych, zalecanym sposobem wykonania tej czynności jest użycie kontraktu komunikatu — pozwala to uniknąć niepotrzebnych poziomów zawijania w wynikowym kodzie XML. Ponadto kontrakty komunikatów umożliwiają większą kontrolę nad wynikowymi komunikatami. Na przykład można zdecydować, które fragmenty informacji powinny znajdować się w treści wiadomości, a które powinny znajdować się w nagłówkach wiadomości. W poniższym przykładzie przedstawiono użycie kontraktów komunikatów.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Używanie kontraktów komunikatów](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 W poprzednim przykładzie Klasa <xref:System.Runtime.Serialization.DataContractSerializer> jest nadal używana domyślnie. Klasy <xref:System.Xml.Serialization.XmlSerializer> można również używać z kontraktami komunikatów. W tym celu zastosuj atrybut <xref:System.ServiceModel.XmlSerializerFormatAttribute> do operacji lub kontraktu, a następnie użyj typów zgodnych z klasą <xref:System.Xml.Serialization.XmlSerializer> w nagłówkach wiadomości i elementach członkowskich treści.  
  
## <a name="describing-messages-by-using-streams"></a>Opisywanie komunikatów przy użyciu strumieni  
 Innym sposobem opisywania komunikatów w operacjach jest użycie klasy <xref:System.IO.Stream> lub jednej z jej klas pochodnych w kontrakcie operacji lub jako element członkowski treści kontraktu wiadomości (musi to być jedyny element członkowski w tym przypadku). W przypadku wiadomości przychodzących typ musi być `Stream`— nie można używać klas pochodnych.  
  
 Zamiast wywoływania serializatora program WCF pobiera dane ze strumienia i umieszcza je bezpośrednio w wiadomości wychodzącej lub pobiera dane z wiadomości przychodzącej i umieszcza je bezpośrednio w strumieniu. Poniższy przykład pokazuje użycie strumieni.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nie można połączyć `Stream` i danych niestrumieniowych w jednej treści wiadomości. Użyj kontraktu komunikatu, aby umieścić dodatkowe dane w nagłówkach wiadomości. Poniższy przykład pokazuje nieprawidłowe użycie strumieni podczas definiowania kontraktu operacji.  
  
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
  
 Poniższy przykład pokazuje prawidłowe użycie strumieni podczas definiowania kontraktu operacji.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [dane dotyczące dużych ilości danych i przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Używanie klasy Message  
 Aby uzyskać pełną kontrolę programistyczną nad komunikatami wysyłanymi lub odbieranymi, można użyć klasy <xref:System.ServiceModel.Channels.Message> bezpośrednio, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Jest to zaawansowany scenariusz, który opisano szczegółowo w temacie [using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Opisywanie komunikatów o błędach  
 Oprócz komunikatów, które są opisane przez wartość zwracaną i parametry wyjściowe lub odwołania, każda operacja, która nie jest jednokierunkowa, może zwracać co najmniej dwie możliwe komunikaty: normalny komunikat odpowiedzi i komunikat o błędzie. Rozważmy następujący kontrakt operacji.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Ta operacja może spowodować zwrócenie zwykłego komunikatu zawierającego numer `float` lub komunikat o błędzie zawierający kod błędu i opis. Można to zrobić, zgłaszając <xref:System.ServiceModel.FaultException> w implementacji usługi.  
  
 Można określić dodatkowe komunikaty o błędach przy użyciu atrybutu <xref:System.ServiceModel.FaultContractAttribute>. Dodatkowe błędy należy serializować przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Te dodatkowe błędy mogą być generowane przez wygenerowanie <xref:System.ServiceModel.FaultException%601> odpowiedniego typu kontraktu danych. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Nie można użyć klasy <xref:System.Xml.Serialization.XmlSerializer> do opisywania błędów. <xref:System.ServiceModel.XmlSerializerFormatAttribute> nie ma wpływu na kontrakty na błędy.  
  
## <a name="using-derived-types"></a>Używanie typów pochodnych  
 Możesz chcieć użyć typu podstawowego w operacji lub w kontrakcie komunikatu, a następnie użyć typu pochodnego podczas rzeczywistego wywoływania operacji. W takim przypadku należy użyć atrybutu <xref:System.ServiceModel.ServiceKnownTypeAttribute> lub innego mechanizmu alternatywnego, aby zezwolić na korzystanie z typów pochodnych. Rozważ wykonanie poniższej operacji.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Załóżmy, że dwa typy, `Book` i `Magazine`, pochodzą od `LibraryItem`. Aby użyć tych typów w operacji `IsLibraryItemAvailable`, można zmienić operację w następujący sposób:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatywnie, można użyć atrybutu <xref:System.Runtime.Serialization.KnownTypeAttribute>, gdy domyślny <xref:System.Runtime.Serialization.DataContractSerializer> jest używany, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Przy użyciu <xref:System.Xml.Serialization.XmlSerializer>można użyć atrybutu <xref:System.Xml.Serialization.XmlIncludeAttribute>.  
  
 Można zastosować atrybut <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operacji lub do całej usługi. Akceptuje typ lub nazwę metody do wywołania, aby uzyskać listę znanych typów, podobnie jak atrybut <xref:System.Runtime.Serialization.KnownTypeAttribute>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Określanie użycia i stylu  
 Podczas opisywania usług przy użyciu Web Services Description Language (WSDL) dwa powszechnie używane style to dokumenty i zdalne wywoływanie procedur (RPC). W stylu dokumentu cała treść komunikatu jest opisana przy użyciu schematu, a WSDL opisuje różne części treści komunikatów, odwołując się do elementów w tym schemacie. W stylu RPC, WSDL odwołuje się do typu schematu dla każdej części wiadomości zamiast elementu. W niektórych przypadkach trzeba ręcznie wybrać jeden z tych stylów. Można to zrobić, stosując atrybut <xref:System.ServiceModel.DataContractFormatAttribute> i ustawiając właściwość `Style` (gdy <xref:System.Runtime.Serialization.DataContractSerializer> jest używana) lub ustawiając `Style` w atrybucie <xref:System.ServiceModel.XmlSerializerFormatAttribute> (w przypadku korzystania z <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Ponadto <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwie formy serializowanych XML: `Literal` i `Encoded`. `Literal` jest najczęściej zaakceptowanym formularzem i jest jedynym formularzem, który obsługuje <xref:System.Runtime.Serialization.DataContractSerializer>. `Encoded` jest starszym formularzem opisanym w sekcji 5 specyfikacji protokołu SOAP i nie jest zalecany w przypadku nowych usług. Aby przełączyć się do trybu `Encoded`, ustaw właściwość `Use` w atrybucie <xref:System.ServiceModel.XmlSerializerFormatAttribute> na `Encoded`.  
  
 W większości przypadków nie należy zmieniać ustawień domyślnych dla `Style` i `Use` właściwości.  
  
## <a name="controlling-the-serialization-process"></a>Kontrolowanie procesu serializacji  
 Aby dostosować sposób serializacji danych, można wykonać kilka czynności.  
  
### <a name="changing-server-serialization-settings"></a>Zmienianie ustawień serializacji serwera  
 Gdy domyślne <xref:System.Runtime.Serialization.DataContractSerializer> jest w użyciu, można kontrolować niektóre aspekty procesu serializacji w usłudze, stosując atrybut <xref:System.ServiceModel.ServiceBehaviorAttribute> do usługi. W celu ustawienia limitu przydziału, który ogranicza maksymalną liczbę obiektów <xref:System.Runtime.Serialization.DataContractSerializer> deserializacji, można użyć właściwości `MaxItemsInObjectGraph`. Za pomocą właściwości `IgnoreExtensionDataObject` można wyłączyć funkcję obsługi wersji okrężnej. Aby uzyskać więcej informacji na temat przydziałów, zobacz [zagadnienia dotyczące zabezpieczeń danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Aby uzyskać więcej informacji na temat rundy, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 W programie WCF dostępne są dwa zachowania, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>, które są automatycznie podłączane, w zależności od tego, który serializator jest używany dla danej operacji. Ponieważ te zachowania są stosowane automatycznie, zazwyczaj nie trzeba ich znać.  
  
 Jednak `DataContractSerializerOperationBehavior` ma właściwości `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`i `DataContractSurrogate`, które mogą być używane do dostosowywania procesu serializacji. Pierwsze dwie właściwości mają takie samo znaczenie jak omówione w poprzedniej sekcji. Można użyć właściwości `DataContractSurrogate`, aby włączyć surogaty kontraktu danych, który jest zaawansowanym mechanizmem do dostosowywania i rozszerzania procesu serializacji. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 `DataContractSerializerOperationBehavior` można użyć do dostosowania serializacji klienta i serwera. Poniższy przykład pokazuje, jak zwiększyć przydział `MaxItemsInObjectGraph` na kliencie.  
  
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
  
Poniżej znajduje się odpowiedni kod w usłudze w przypadku samodzielnego udostępniania:
  
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
  
 W przypadku przypadków hostowanych w sieci Web należy utworzyć nową klasę pochodną `ServiceHost` i użyć fabryki hosta usługi, aby ją podłączyć.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Kontrolowanie ustawień serializacji w konfiguracji  
 `MaxItemsInObjectGraph` i `IgnoreExtensionDataObject` mogą być kontrolowane przez konfigurację przy użyciu punktu końcowego `dataContractSerializer` lub zachowania usługi, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serializacja typu udostępnionego, zachowywania grafu obiektów i serializatorów niestandardowych  
 <xref:System.Runtime.Serialization.DataContractSerializer> serializować przy użyciu nazw kontraktów danych, a nie nazw typu .NET. Jest to zgodne z architekturą zorientowaną na usługę założenia i umożliwia zapewnienie doskonałej elastyczności — typy .NET mogą ulec zmianie bez wpływu na umowę sieciową. W rzadkich przypadkach możesz chcieć serializować rzeczywiste nazwy typu .NET, co wprowadza ścisłe sprzężenie między klientem a serwerem, podobnie jak technologia komunikacji zdalnej .NET Framework. Nie jest to zalecane rozwiązanie, z wyjątkiem rzadkich przypadków, które zazwyczaj występują podczas migracji do programu WCF z .NET Framework komunikacji zdalnej. W takim przypadku należy użyć klasy <xref:System.Runtime.Serialization.NetDataContractSerializer> zamiast klasy <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> zwykle serializować wykresy obiektów jako drzewa obiektów. Oznacza to, że jeśli ten sam obiekt jest odwołuje się więcej niż raz, jest serializowany więcej niż jeden raz. Rozważmy na przykład wystąpienie `PurchaseOrder`, które ma dwa pola typu adres o nazwie `billTo` i `shipTo`. Jeśli oba pola są ustawione na to samo wystąpienie adresu, istnieją dwa identyczne wystąpienia adresów po serializacji i deserializacji. Jest to realizowane z powodu braku interoperacyjności standardowej do reprezentowania grafów obiektów w kodzie XML (z wyjątkiem starszej wersji protokołu SOAP w <xref:System.Xml.Serialization.XmlSerializer>, zgodnie z opisem w poprzedniej sekcji na `Style` i `Use`). Serializacja grafów obiektów jako drzew ma pewne wady, na przykład wykresy z odwołaniami cyklicznymi nie mogą być serializowane. Czasami konieczne jest przełączenie na prawdziwą Serializacja grafu obiektów, nawet jeśli nie jest to możliwe. Można to zrobić przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> skonstruowane z parametrem `preserveObjectReferences` ustawionym na `true`.  
  
 Czasami wbudowane serializatory są niewystarczające dla Twojego scenariusza. W większości przypadków można nadal używać abstrakcji <xref:System.Runtime.Serialization.XmlObjectSerializer>, z której pochodzi zarówno <xref:System.Runtime.Serialization.DataContractSerializer>, jak i <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
 W poprzednich trzech przypadkach (zachowywanie typu .NET, zachowywanie grafu obiektów i całkowicie niestandardowa Serializacja oparta na `XmlObjectSerializer`) wszystkie wymagają, aby niestandardowa serializator był podłączony. W tym celu wykonaj następujące czynności:  
  
1. Napisz własne zachowanie wynikające z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2. Zastąp dwie `CreateSerializer` metody, aby zwrócić swój serializator (<xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> z `preserveObjectReferences` ustawionym na `true`lub własne niestandardowe <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3. Przed otwarciem hosta usługi lub utworzeniem kanału klienta należy usunąć istniejące zachowanie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i podłączyć niestandardową klasę pochodną utworzoną w poprzednich krokach.  
  
 Aby uzyskać więcej informacji na temat zaawansowanych koncepcji serializacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Zobacz także

- [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Instrukcje: włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
