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
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="36687-102">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="36687-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="36687-103">Windows Communication Foundation (WCF) można traktować jako infrastruktury obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="36687-104">Operacje serwisowe mogą odbierać wiadomości, przetwarzać je i wysyłać im wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="36687-105">Komunikaty są opisane przy użyciu kontraktów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="36687-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="36687-106">Rozważmy na przykład następującą umowę.</span><span class="sxs-lookup"><span data-stu-id="36687-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="36687-107">W tym `GetAirfare` miejscu operacja akceptuje wiadomość `fromCity` `toCity`z informacjami o i , a następnie zwraca komunikat, który zawiera numer.</span><span class="sxs-lookup"><span data-stu-id="36687-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="36687-108">W tym temacie wyjaśniono różne sposoby, w których umowa operacji może opisywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="36687-109">Opisywanie wiadomości przy użyciu parametrów</span><span class="sxs-lookup"><span data-stu-id="36687-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="36687-110">Najprostszym sposobem opisania wiadomości jest użycie listy parametrów i zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="36687-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="36687-111">W poprzednim przykładzie `fromCity` parametry `toCity` i ciąg zostały użyte do opisania komunikatu żądania, a wartość zwracana float została użyta do opisania wiadomości odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="36687-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="36687-112">Jeśli sama zwracana wartość nie wystarczy do opisania wiadomości odpowiedzi, mogą być używane parametry out.</span><span class="sxs-lookup"><span data-stu-id="36687-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="36687-113">Na przykład następująca `fromCity` operacja `toCity` ma i w komunikacie żądania i numer wraz z walutą w komunikacie odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="36687-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="36687-114">Ponadto można użyć parametrów odwołania, aby parametr część żądania i odpowiedzi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="36687-115">Parametry muszą być typów, które mogą być serializowane (konwertowane na XML).</span><span class="sxs-lookup"><span data-stu-id="36687-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="36687-116">Domyślnie WCF używa składnika <xref:System.Runtime.Serialization.DataContractSerializer> o nazwie klasy do wykonywania tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="36687-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="36687-117">Większość typów pierwotnych (takich `string` `float`jak `int` `DateTime`, , i .) są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="36687-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="36687-118">Typy zdefiniowane przez użytkownika muszą zwykle mieć kontrakt na dane.</span><span class="sxs-lookup"><span data-stu-id="36687-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="36687-119">Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="36687-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="36687-120">Od czasu `DataContractSerializer` do czasu nie jest odpowiedni do serializacji typów.</span><span class="sxs-lookup"><span data-stu-id="36687-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="36687-121">WCF obsługuje alternatywny aparat serializacji, <xref:System.Xml.Serialization.XmlSerializer>, który można również użyć do serializacji parametrów.</span><span class="sxs-lookup"><span data-stu-id="36687-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="36687-122">Umożliwia <xref:System.Xml.Serialization.XmlSerializer> użycie większej kontroli nad wynikowego pliku XML `XmlAttributeAttribute`przy użyciu atrybutów, takich jak .</span><span class="sxs-lookup"><span data-stu-id="36687-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="36687-123">Aby przełączyć <xref:System.Xml.Serialization.XmlSerializer> się do korzystania z dla określonej <xref:System.ServiceModel.XmlSerializerFormatAttribute> operacji lub dla całej usługi, należy zastosować atrybut do operacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="36687-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="36687-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="36687-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="36687-125">Aby uzyskać więcej informacji, zobacz [Korzystanie z klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="36687-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="36687-126">Pamiętaj, że ręczne <xref:System.Xml.Serialization.XmlSerializer> przełączanie do jak pokazano tutaj nie jest zalecane, chyba że masz konkretne powody, aby to zrobić, jak opisano w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="36687-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="36687-127">Aby wyizolować nazwy parametrów .NET od nazw `Name` umów, można użyć atrybutu <xref:System.ServiceModel.MessageParameterAttribute> i użyć właściwości, aby ustawić nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="36687-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="36687-128">Na przykład następująca umowa operacji jest odpowiednikiem pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="36687-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="36687-129">Opisywanie pustych wiadomości</span><span class="sxs-lookup"><span data-stu-id="36687-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="36687-130">Pusty komunikat żądania można opisać, nie mając żadnych parametrów wejściowych lub referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="36687-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="36687-131">Na przykład w języku C#:</span><span class="sxs-lookup"><span data-stu-id="36687-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="36687-132">Na przykład w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="36687-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="36687-133">Pustą wiadomość odpowiedzi można opisać, `void` mając typ zwracany i nie ma parametrów wyjściowych lub referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="36687-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="36687-134">Na przykład w:</span><span class="sxs-lookup"><span data-stu-id="36687-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="36687-135">Różni się to od operacji jednokierunkowej, takiej jak:</span><span class="sxs-lookup"><span data-stu-id="36687-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="36687-136">Operacja `SetTemperatureStatus` zwraca pustą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="36687-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="36687-137">Zamiast tego może zwrócić błąd, jeśli występuje problem z przetwarzaniem komunikatu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="36687-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="36687-138">Operacja `SetLightbulbStatus` zwraca nic.</span><span class="sxs-lookup"><span data-stu-id="36687-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="36687-139">Nie ma sposobu, aby poinformować o stanie usterki z tej operacji.</span><span class="sxs-lookup"><span data-stu-id="36687-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="36687-140">Opisywanie wiadomości przy użyciu kontraktów wiadomości</span><span class="sxs-lookup"><span data-stu-id="36687-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="36687-141">Można użyć jednego typu do reprezentowania całej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="36687-142">Chociaż jest możliwe użycie umowy danych w tym celu, zalecanym sposobem, aby to zrobić, jest użycie kontraktu wiadomości — pozwala to uniknąć niepotrzebnych poziomów zawijania w wynikowym pliku XML.</span><span class="sxs-lookup"><span data-stu-id="36687-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="36687-143">Ponadto kontrakty wiadomości umożliwiają sprawowanie większej kontroli nad wiadomościami wynikowymi.</span><span class="sxs-lookup"><span data-stu-id="36687-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="36687-144">Na przykład można zdecydować, które informacje powinny znajdować się w treści wiadomości, a które powinny znajdować się w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="36687-145">W poniższym przykładzie przedstawiono użycie kontraktów wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="36687-146">Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów na wiadomości](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="36687-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="36687-147">W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> klasa jest nadal używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="36687-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="36687-148">Klasa <xref:System.Xml.Serialization.XmlSerializer> może być również używana z kontraktami wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="36687-149">Aby to zrobić, <xref:System.ServiceModel.XmlSerializerFormatAttribute> zastosuj atrybut do operacji lub umowy i użyj <xref:System.Xml.Serialization.XmlSerializer> typów zgodnych z klasą w nagłówkach wiadomości i elementów członkowskich treści.</span><span class="sxs-lookup"><span data-stu-id="36687-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="36687-150">Opisywanie wiadomości przy użyciu strumieni</span><span class="sxs-lookup"><span data-stu-id="36687-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="36687-151">Innym sposobem opisywania komunikatów w <xref:System.IO.Stream> operacjach jest użycie klasy lub jednej z jej klas pochodnych w umowie operacji lub jako elementu umowy wiadomości (musi być jedynym elementem członkowskim w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="36687-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="36687-152">W przypadku wiadomości przychodzących `Stream`typem musi być — nie można używać klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="36687-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="36687-153">Zamiast wywoływać serializatora, WCF pobiera dane ze strumienia i umieszcza je bezpośrednio w wiadomości wychodzącej lub pobiera dane z wiadomości przychodzącej i umieszcza je bezpośrednio w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="36687-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="36687-154">Poniższy przykład pokazuje użycie strumieni.</span><span class="sxs-lookup"><span data-stu-id="36687-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="36687-155">Nie można `Stream` łączyć i nie przesyłać strumieniowo danych w treści pojedynczej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="36687-156">Użyj umowy wiadomości, aby umieścić dodatkowe dane w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36687-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="36687-157">Poniższy przykład pokazuje niepoprawne użycie strumieni podczas definiowania umowy operacji.</span><span class="sxs-lookup"><span data-stu-id="36687-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="36687-158">W poniższym przykładzie przedstawiono prawidłowe użycie strumieni podczas definiowania umowy operacji.</span><span class="sxs-lookup"><span data-stu-id="36687-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="36687-159">Aby uzyskać więcej informacji, zobacz [Duże dane i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="36687-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="36687-160">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="36687-160">Using the Message Class</span></span>  
 <span data-ttu-id="36687-161">Aby mieć pełną kontrolę programową nad wiadomościami <xref:System.ServiceModel.Channels.Message> wysłanymi lub odebranymi, można użyć klasy bezpośrednio, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="36687-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="36687-162">Jest to zaawansowany scenariusz, który jest szczegółowo opisany w [using message class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="36687-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="36687-163">Opisywanie komunikatów o błędach</span><span class="sxs-lookup"><span data-stu-id="36687-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="36687-164">Oprócz komunikatów, które są opisane przez wartość zwracaną i parametrów wyjściowych lub referencyjnych, każda operacja, która nie jest jednokierunkowa, może zwrócić co najmniej dwa możliwe komunikaty: jego normalny komunikat odpowiedzi i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="36687-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="36687-165">Należy wziąć pod uwagę następującą umowę operacji.</span><span class="sxs-lookup"><span data-stu-id="36687-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="36687-166">Ta operacja może zwrócić normalny komunikat `float` zawierający numer lub komunikat o błędzie zawierający kod usterki i opis.</span><span class="sxs-lookup"><span data-stu-id="36687-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="36687-167">Można to osiągnąć, rzucając <xref:System.ServiceModel.FaultException> w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="36687-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="36687-168">Można określić dodatkowe możliwe komunikaty o błędach przy użyciu atrybutu. <xref:System.ServiceModel.FaultContractAttribute></span><span class="sxs-lookup"><span data-stu-id="36687-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="36687-169">Dodatkowe błędy muszą być serializable <xref:System.Runtime.Serialization.DataContractSerializer>przy użyciu , jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="36687-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="36687-170">Te dodatkowe błędy mogą być generowane <xref:System.ServiceModel.FaultException%601> przez rzutowanie odpowiedniego typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="36687-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="36687-171">Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków i usterek](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="36687-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="36687-172">Nie można <xref:System.Xml.Serialization.XmlSerializer> użyć klasy do opisania błędów.</span><span class="sxs-lookup"><span data-stu-id="36687-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="36687-173">Nie <xref:System.ServiceModel.XmlSerializerFormatAttribute> ma to wpływu na umowy o usterkę.</span><span class="sxs-lookup"><span data-stu-id="36687-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="36687-174">Korzystanie z typów pochodnych</span><span class="sxs-lookup"><span data-stu-id="36687-174">Using Derived Types</span></span>  
 <span data-ttu-id="36687-175">Można użyć typu podstawowego w operacji lub umowy wiadomości, a następnie użyć typu pochodnego podczas faktycznie wywoływania operacji.</span><span class="sxs-lookup"><span data-stu-id="36687-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="36687-176">W takim przypadku należy użyć <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub innego alternatywnego mechanizmu, aby umożliwić użycie typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="36687-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="36687-177">Należy wziąć pod uwagę następującą operację.</span><span class="sxs-lookup"><span data-stu-id="36687-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="36687-178">Załóżmy, `Book` że `Magazine`dwa typy i , pochodzą od `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="36687-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="36687-179">Aby użyć tych `IsLibraryItemAvailable` typów w operacji, można zmienić operację w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="36687-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="36687-180">Alternatywnie można użyć <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu, gdy <xref:System.Runtime.Serialization.DataContractSerializer> jest używany wartość domyślna, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="36687-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="36687-181">Można użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu podczas <xref:System.Xml.Serialization.XmlSerializer>korzystania z pliku .</span><span class="sxs-lookup"><span data-stu-id="36687-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="36687-182">Można zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybut do operacji lub do całej usługi.</span><span class="sxs-lookup"><span data-stu-id="36687-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="36687-183">Akceptuje typ lub nazwę metody do wywołania, aby uzyskać listę znanych typów, <xref:System.Runtime.Serialization.KnownTypeAttribute> podobnie jak atrybut.</span><span class="sxs-lookup"><span data-stu-id="36687-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="36687-184">Aby uzyskać więcej informacji, zobacz [Znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="36687-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="36687-185">Określanie sposobu użycia i stylu</span><span class="sxs-lookup"><span data-stu-id="36687-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="36687-186">Opisując usługi przy użyciu języka opisu usług sieci Web (WSDL), dwa powszechnie używane style to Document and remote procedure call (RPC).</span><span class="sxs-lookup"><span data-stu-id="36687-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="36687-187">W stylu Dokumentu cała treść wiadomości jest opisana przy użyciu schematu, a WSDL opisuje różne części treści wiadomości, odwołując się do elementów w tym schemacie.</span><span class="sxs-lookup"><span data-stu-id="36687-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="36687-188">W stylu RPC WSDL odwołuje się do typu schematu dla każdej części wiadomości, a nie elementu.</span><span class="sxs-lookup"><span data-stu-id="36687-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="36687-189">W niektórych przypadkach należy ręcznie wybrać jeden z tych stylów.</span><span class="sxs-lookup"><span data-stu-id="36687-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="36687-190">Można to zrobić, stosując <xref:System.ServiceModel.DataContractFormatAttribute> atrybut i `Style` ustawiając właściwość <xref:System.Runtime.Serialization.DataContractSerializer> (gdy jest `Style` używana) <xref:System.ServiceModel.XmlSerializerFormatAttribute> lub ustawiając <xref:System.Xml.Serialization.XmlSerializer>atrybut (podczas korzystania z ).</span><span class="sxs-lookup"><span data-stu-id="36687-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="36687-191">Dodatkowo <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwie formy serializowanego XML: `Literal` i `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="36687-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="36687-192">`Literal`jest najczęściej akceptowanym formularzem i jest jedyną formą podpory. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="36687-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="36687-193">`Encoded`jest starszą formą opisaną w sekcji 5 specyfikacji PROTOKOŁU SOAP i nie jest zalecana w przypadku nowych usług.</span><span class="sxs-lookup"><span data-stu-id="36687-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="36687-194">Aby przełączyć `Encoded` się `Use` do trybu, ustaw właściwość atrybutu <xref:System.ServiceModel.XmlSerializerFormatAttribute> . `Encoded`</span><span class="sxs-lookup"><span data-stu-id="36687-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="36687-195">W większości przypadków nie należy zmieniać ustawień `Style` `Use` domyślnych dla i właściwości.</span><span class="sxs-lookup"><span data-stu-id="36687-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="36687-196">Kontrolowanie procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="36687-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="36687-197">Można wykonać wiele czynności, aby dostosować sposób serializacji danych.</span><span class="sxs-lookup"><span data-stu-id="36687-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="36687-198">Zmiana ustawień serializacji serwera</span><span class="sxs-lookup"><span data-stu-id="36687-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="36687-199">Gdy wartość <xref:System.Runtime.Serialization.DataContractSerializer> domyślna jest w użyciu, można kontrolować niektóre aspekty procesu <xref:System.ServiceModel.ServiceBehaviorAttribute> serializacji w usłudze, stosując atrybut do usługi.</span><span class="sxs-lookup"><span data-stu-id="36687-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="36687-200">W szczególności można użyć `MaxItemsInObjectGraph` właściwości, aby ustawić przydział, który <xref:System.Runtime.Serialization.DataContractSerializer> ogranicza maksymalną liczbę obiektów deserializes.</span><span class="sxs-lookup"><span data-stu-id="36687-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="36687-201">Za pomocą `IgnoreExtensionDataObject` tej właściwości można wyłączyć funkcję usuwania wersji zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="36687-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="36687-202">Aby uzyskać więcej informacji na temat przydziałów, zobacz [Zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="36687-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="36687-203">Aby uzyskać więcej informacji na temat potknięcia zaokrąglania, zobacz [Kontrakty danych zgodne z przekazywaniem](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="36687-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="36687-204">Zachowania serializacji</span><span class="sxs-lookup"><span data-stu-id="36687-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="36687-205">Dwa zachowania są dostępne w WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> które są automatycznie podłączone w zależności od serializatora jest używany dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="36687-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="36687-206">Ponieważ te zachowania są stosowane automatycznie, zwykle nie trzeba być świadomym ich.</span><span class="sxs-lookup"><span data-stu-id="36687-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="36687-207">Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`i `DataContractSurrogate` właściwości, które można użyć do dostosowania procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="36687-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="36687-208">Pierwsze dwie właściwości mają takie samo znaczenie, jak omówiono w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="36687-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="36687-209">Właściwości można `DataContractSurrogate` użyć, aby włączyć zastępcze umowy danych, które są potężnym mechanizmem dostosowywania i rozszerzania procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="36687-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="36687-210">Aby uzyskać więcej informacji, zobacz [Zastępcze umowy danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="36687-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="36687-211">Można użyć, `DataContractSerializerOperationBehavior` aby dostosować zarówno serializacji klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="36687-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="36687-212">W poniższym przykładzie `MaxItemsInObjectGraph` pokazano, jak zwiększyć przydział na kliencie.</span><span class="sxs-lookup"><span data-stu-id="36687-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="36687-213">Poniżej znajduje się równoważny kod w usłudze, w przypadku hostowane samodzielnie:</span><span class="sxs-lookup"><span data-stu-id="36687-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="36687-214">W przypadku hostowanego w sieci Web `ServiceHost` należy utworzyć nową klasę pochodną i użyć fabryki hosta usług, aby ją podłączyć.</span><span class="sxs-lookup"><span data-stu-id="36687-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="36687-215">Kontrolowanie ustawień serializacji w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="36687-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="36687-216">I mogą być kontrolowane za `dataContractSerializer` pomocą konfiguracji przy użyciu zachowania punktu końcowego lub usługi, jak pokazano w poniższym przykładzie. `IgnoreExtensionDataObject` `MaxItemsInObjectGraph`</span><span class="sxs-lookup"><span data-stu-id="36687-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="36687-217">Serializacja typu udostępnionego, zachowanie wykresu obiektów i serializatory niestandardowe</span><span class="sxs-lookup"><span data-stu-id="36687-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="36687-218">Serializes <xref:System.Runtime.Serialization.DataContractSerializer> przy użyciu nazw kontraktów danych, a nie nazw typów .NET.</span><span class="sxs-lookup"><span data-stu-id="36687-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="36687-219">Jest to zgodne z zasadami architektury zorientowanych na usługi i pozwala na duży stopień elastyczności — typy .NET mogą się zmieniać bez wpływu na kontrakt przewodowy.</span><span class="sxs-lookup"><span data-stu-id="36687-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="36687-220">W rzadkich przypadkach można serializować rzeczywiste nazwy typów .NET, wprowadzając w ten sposób ścisłe sprzężenie między klientem a serwerem, podobne do technologii komunikacji zdalnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36687-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="36687-221">Nie jest to zalecana praktyka, z wyjątkiem rzadkich przypadków, które zwykle występują podczas migracji do WCF z .NET Framework komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="36687-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="36687-222">W takim przypadku należy <xref:System.Runtime.Serialization.NetDataContractSerializer> użyć klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="36687-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="36687-223">Zwykle <xref:System.Runtime.Serialization.DataContractSerializer> serializuje wykresy obiektów jako drzewa obiektów.</span><span class="sxs-lookup"><span data-stu-id="36687-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="36687-224">Oznacza to, że jeśli ten sam obiekt jest określany więcej niż jeden raz, jest serializowany więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="36687-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="36687-225">Rozważmy na `PurchaseOrder` przykład wystąpienie, które ma `billTo` `shipTo`dwa pola typu Adres wywoływany i .</span><span class="sxs-lookup"><span data-stu-id="36687-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="36687-226">Jeśli oba pola są ustawione na to samo wystąpienie Address, istnieją dwa identyczne wystąpienia adresu po serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="36687-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="36687-227">Odbywa się to, ponieważ nie istnieje standardowy interoperacyjny sposób reprezentowania wykresów obiektów w formacie <xref:System.Xml.Serialization.XmlSerializer>XML (z wyjątkiem starszego standardu zakodowanego w formacie SOAP dostępnego w , jak opisano w poprzedniej sekcji na `Style` i `Use`).</span><span class="sxs-lookup"><span data-stu-id="36687-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="36687-228">Serializowanie wykresów obiektów jako drzew ma pewne wady, na przykład wykresy z odwołaniami cyklicznymi nie mogą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="36687-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="36687-229">Od czasu do czasu konieczne jest przełączenie się do serializacji wykresu obiektu true, nawet jeśli nie jest interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="36687-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="36687-230">Można to zrobić za <xref:System.Runtime.Serialization.DataContractSerializer> pomocą skonstruowane z parametrem ustawionym `preserveObjectReferences` na `true`.</span><span class="sxs-lookup"><span data-stu-id="36687-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="36687-231">Od czasu do czasu wbudowane serializatory nie są wystarczające dla scenariusza.</span><span class="sxs-lookup"><span data-stu-id="36687-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="36687-232">W większości przypadków można nadal <xref:System.Runtime.Serialization.XmlObjectSerializer> używać abstrakcji, <xref:System.Runtime.Serialization.NetDataContractSerializer> z której zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i pochodne.</span><span class="sxs-lookup"><span data-stu-id="36687-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="36687-233">Poprzednie trzy przypadki (.NET zachowanie typu, zachowanie wykresu obiektu i całkowicie niestandardowe `XmlObjectSerializer`serializacji) wszystkie wymagają niestandardowego serializatora być podłączone.</span><span class="sxs-lookup"><span data-stu-id="36687-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="36687-234">W tym celu wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="36687-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="36687-235">Napisz własne zachowanie wynikające <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>z .</span><span class="sxs-lookup"><span data-stu-id="36687-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="36687-236">Zastąp `CreateSerializer` dwie metody zwracania własnego <xref:System.Runtime.Serialization.NetDataContractSerializer>serializatora <xref:System.Runtime.Serialization.DataContractSerializer> (albo , z `preserveObjectReferences` zestawem do `true`, lub własne niestandardowe). <xref:System.Runtime.Serialization.XmlObjectSerializer></span><span class="sxs-lookup"><span data-stu-id="36687-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="36687-237">Przed otwarciem hosta usługi lub utworzeniem <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> kanału klienta usuń istniejące zachowanie i podłącz niestandardową klasę pochodną utworzoną w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="36687-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="36687-238">Aby uzyskać więcej informacji na temat zaawansowanych koncepcji serializacji, zobacz [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="36687-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36687-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36687-239">See also</span></span>

- [<span data-ttu-id="36687-240">Używanie klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="36687-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="36687-241">Instrukcje: włączanie przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="36687-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="36687-242">Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="36687-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
