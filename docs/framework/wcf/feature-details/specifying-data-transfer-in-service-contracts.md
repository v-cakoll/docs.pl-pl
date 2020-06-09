---
title: Określanie transferu danych w kontraktach usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: ae05fb5ea0ee4962d9889e2a29399a3913a0d9d5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600299"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="67946-102">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="67946-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="67946-103">Windows Communication Foundation (WCF) można traktować jako infrastrukturę obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="67946-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="67946-104">Operacje usługi mogą odbierać komunikaty, przetwarzać je i wysyłać do nich komunikaty.</span><span class="sxs-lookup"><span data-stu-id="67946-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="67946-105">Komunikaty są opisane przy użyciu kontraktów operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="67946-106">Rozważmy na przykład następujący kontrakt.</span><span class="sxs-lookup"><span data-stu-id="67946-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="67946-107">W tym miejscu `GetAirfare` operacja akceptuje komunikat z informacjami o `fromCity` i `toCity` , a następnie zwraca komunikat zawierający liczbę.</span><span class="sxs-lookup"><span data-stu-id="67946-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="67946-108">W tym temacie wyjaśniono różne sposoby opisywania komunikatów przez kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="67946-109">Opisywanie komunikatów przy użyciu parametrów</span><span class="sxs-lookup"><span data-stu-id="67946-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="67946-110">Najprostszym sposobem opisywania wiadomości jest użycie listy parametrów i wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="67946-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="67946-111">W poprzednim przykładzie `fromCity` `toCity` Parametry i parametrów zostały użyte do opisania komunikatu żądania, a wartość zwracana zmiennoprzecinkowa została użyta do opisania komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="67946-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="67946-112">Jeśli wartość zwracana jest zbyt mała, aby opisać komunikat odpowiedzi, można użyć parametrów out.</span><span class="sxs-lookup"><span data-stu-id="67946-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="67946-113">Na przykład następująca operacja zawiera `fromCity` i `toCity` w jego komunikacie żądania oraz liczbę wraz z walutą w swojej wiadomości odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="67946-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="67946-114">Ponadto możesz użyć parametrów odwołania, aby utworzyć część parametru zarówno żądania, jak i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="67946-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="67946-115">Parametry muszą być typami, które mogą być serializowane (konwertowane na XML).</span><span class="sxs-lookup"><span data-stu-id="67946-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="67946-116">Domyślnie WCF używa składnika zwanego <xref:System.Runtime.Serialization.DataContractSerializer> klasą w celu wykonania tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="67946-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="67946-117">Obsługiwane są większość typów pierwotnych (takich jak `int` ,, `string` `float` i `DateTime` .).</span><span class="sxs-lookup"><span data-stu-id="67946-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="67946-118">Typy zdefiniowane przez użytkownika muszą zwykle mieć kontrakt danych.</span><span class="sxs-lookup"><span data-stu-id="67946-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="67946-119">Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="67946-119">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="67946-120">Czasami `DataContractSerializer` nie jest wystarczające do serializacji typów.</span><span class="sxs-lookup"><span data-stu-id="67946-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="67946-121">Usługa WCF obsługuje alternatywny aparat serializacji, <xref:System.Xml.Serialization.XmlSerializer> którego można również użyć do serializacji parametrów.</span><span class="sxs-lookup"><span data-stu-id="67946-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="67946-122"><xref:System.Xml.Serialization.XmlSerializer>Umożliwia użycie większej kontroli nad wynikowym kodem XML przy użyciu atrybutów, takich jak `XmlAttributeAttribute` .</span><span class="sxs-lookup"><span data-stu-id="67946-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="67946-123">Aby przełączyć się do użycia <xref:System.Xml.Serialization.XmlSerializer> dla określonej operacji lub dla całej usługi, Zastosuj <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybut do operacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="67946-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="67946-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="67946-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="67946-125">Aby uzyskać więcej informacji, zobacz [Używanie klasy XmlSerializer](using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="67946-125">For more information, see [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="67946-126">Należy pamiętać, że ręczne przełączenie do <xref:System.Xml.Serialization.XmlSerializer> pokazanego tutaj nie jest zalecane, chyba że masz określone przyczyny, zgodnie z opisem w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="67946-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="67946-127">Aby izolować nazwy parametrów .NET z nazw kontraktów, można użyć <xref:System.ServiceModel.MessageParameterAttribute> atrybutu i `Name` ustawić nazwę kontraktu przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="67946-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="67946-128">Na przykład następujący kontrakt operacji jest odpowiednikiem pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="67946-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="67946-129">Opisywanie pustych wiadomości</span><span class="sxs-lookup"><span data-stu-id="67946-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="67946-130">Pusty komunikat żądania może być opisany przez brak parametrów wejściowych lub referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="67946-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="67946-131">Na przykład w języku C#:</span><span class="sxs-lookup"><span data-stu-id="67946-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="67946-132">Na przykład w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="67946-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="67946-133">Pusty komunikat odpowiedzi można opisać poprzez posiadanie `void` zwracanego typu i brak parametrów wyjściowych lub referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="67946-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="67946-134">Na przykład w:</span><span class="sxs-lookup"><span data-stu-id="67946-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="67946-135">Różni się to od operacji jednokierunkowej, na przykład:</span><span class="sxs-lookup"><span data-stu-id="67946-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="67946-136">`SetTemperatureStatus`Operacja zwraca pusty komunikat.</span><span class="sxs-lookup"><span data-stu-id="67946-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="67946-137">Może zwrócić błąd zamiast tego, jeśli wystąpił problem podczas przetwarzania komunikatu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="67946-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="67946-138">`SetLightbulbStatus`Operacja nie zwraca żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="67946-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="67946-139">Nie ma możliwości komunikacji z warunkiem błędu z tej operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="67946-140">Opisywanie komunikatów przy użyciu kontraktów komunikatów</span><span class="sxs-lookup"><span data-stu-id="67946-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="67946-141">Możesz chcieć użyć jednego typu do reprezentowania całej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="67946-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="67946-142">Chociaż istnieje możliwość użycia w tym celu kontraktu danych, zalecanym sposobem wykonania tej czynności jest użycie kontraktu komunikatu — pozwala to uniknąć niepotrzebnych poziomów zawijania w wynikowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="67946-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="67946-143">Ponadto kontrakty komunikatów umożliwiają większą kontrolę nad wynikowymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="67946-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="67946-144">Na przykład można zdecydować, które fragmenty informacji powinny znajdować się w treści wiadomości, a które powinny znajdować się w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="67946-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="67946-145">W poniższym przykładzie przedstawiono użycie kontraktów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="67946-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="67946-146">Aby uzyskać więcej informacji, zobacz [Używanie kontraktów komunikatów](using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="67946-146">For more information, see [Using Message Contracts](using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="67946-147">W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> Klasa jest nadal używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="67946-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="67946-148"><xref:System.Xml.Serialization.XmlSerializer>Klasy można również używać z kontraktami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="67946-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="67946-149">W tym celu Zastosuj <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybut do operacji lub kontraktu, a następnie użyj typów zgodnych z <xref:System.Xml.Serialization.XmlSerializer> klasą w nagłówkach wiadomości i elementach członkowskich treści.</span><span class="sxs-lookup"><span data-stu-id="67946-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="67946-150">Opisywanie komunikatów przy użyciu strumieni</span><span class="sxs-lookup"><span data-stu-id="67946-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="67946-151">Innym sposobem opisywania komunikatów w operacjach jest użycie <xref:System.IO.Stream> klasy lub jednej z jej klas pochodnych w kontrakcie operacji lub jako element członkowski treści kontraktu wiadomości (musi to być jedyny element członkowski w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="67946-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="67946-152">W przypadku wiadomości przychodzących typ musi być `Stream` — nie można używać klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="67946-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="67946-153">Zamiast wywoływania serializatora program WCF pobiera dane ze strumienia i umieszcza je bezpośrednio w wiadomości wychodzącej lub pobiera dane z wiadomości przychodzącej i umieszcza je bezpośrednio w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="67946-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="67946-154">Poniższy przykład pokazuje użycie strumieni.</span><span class="sxs-lookup"><span data-stu-id="67946-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="67946-155">Nie można łączyć `Stream` i nie przesyłać strumieniowo danych w jednej treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="67946-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="67946-156">Użyj kontraktu komunikatu, aby umieścić dodatkowe dane w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="67946-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="67946-157">Poniższy przykład pokazuje nieprawidłowe użycie strumieni podczas definiowania kontraktu operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="67946-158">Poniższy przykład pokazuje prawidłowe użycie strumieni podczas definiowania kontraktu operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="67946-159">Aby uzyskać więcej informacji, zobacz [dane dotyczące dużych ilości danych i przesyłania strumieniowego](large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="67946-159">For more information, see [Large Data and Streaming](large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="67946-160">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="67946-160">Using the Message Class</span></span>  
 <span data-ttu-id="67946-161">Aby uzyskać pełną kontrolę programistyczną nad komunikatami wysyłanymi lub odbieranymi, można użyć <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="67946-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="67946-162">Jest to zaawansowany scenariusz, który opisano szczegółowo w temacie [using the Message Class](using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="67946-162">This is an advanced scenario, which is described in detail in [Using the Message Class](using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="67946-163">Opisywanie komunikatów o błędach</span><span class="sxs-lookup"><span data-stu-id="67946-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="67946-164">Oprócz komunikatów, które są opisane przez wartość zwracaną i parametry wyjściowe lub odwołania, każda operacja, która nie jest jednokierunkowa, może zwracać co najmniej dwie możliwe komunikaty: normalny komunikat odpowiedzi i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="67946-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="67946-165">Rozważmy następujący kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="67946-166">Ta operacja może zwrócić normalny komunikat zawierający `float` liczbę lub komunikat o błędzie, który zawiera kod błędu i opis.</span><span class="sxs-lookup"><span data-stu-id="67946-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="67946-167">Można to osiągnąć przez wyrzucanie <xref:System.ServiceModel.FaultException> w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="67946-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="67946-168">Można określić dodatkowe komunikaty o błędach przy użyciu <xref:System.ServiceModel.FaultContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="67946-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="67946-169">Dodatkowe błędy muszą być możliwe do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> , jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="67946-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="67946-170">Te dodatkowe błędy mogą być generowane przez wyrzucanie <xref:System.ServiceModel.FaultException%601> odpowiedniego typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="67946-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="67946-171">Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków i błędów](../extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="67946-171">For more information, see [Handling Exceptions and Faults](../extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="67946-172">Nie można użyć <xref:System.Xml.Serialization.XmlSerializer> klasy do opisywania błędów.</span><span class="sxs-lookup"><span data-stu-id="67946-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="67946-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute>Nie ma wpływu na kontrakty błędów.</span><span class="sxs-lookup"><span data-stu-id="67946-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="67946-174">Używanie typów pochodnych</span><span class="sxs-lookup"><span data-stu-id="67946-174">Using Derived Types</span></span>  
 <span data-ttu-id="67946-175">Możesz chcieć użyć typu podstawowego w operacji lub w kontrakcie komunikatu, a następnie użyć typu pochodnego podczas rzeczywistego wywoływania operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="67946-176">W takim przypadku należy użyć <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub innego mechanizmu alternatywnego, aby zezwolić na korzystanie z typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="67946-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="67946-177">Rozważ wykonanie poniższej operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="67946-178">Załóżmy, że dwa typy `Book` i `Magazine` , pochodne od `LibraryItem` .</span><span class="sxs-lookup"><span data-stu-id="67946-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="67946-179">Aby użyć tych typów w `IsLibraryItemAvailable` operacji, można zmienić tę operację w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="67946-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="67946-180">Alternatywnie, można użyć atrybutu, <xref:System.Runtime.Serialization.KnownTypeAttribute> gdy wartość domyślna <xref:System.Runtime.Serialization.DataContractSerializer> jest używana, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="67946-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="67946-181">Można użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu podczas korzystania z <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="67946-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="67946-182">Można zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybut do operacji lub do całej usługi.</span><span class="sxs-lookup"><span data-stu-id="67946-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="67946-183">Akceptuje typ lub nazwę metody do wywołania, aby uzyskać listę znanych typów, podobnie jak <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="67946-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="67946-184">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="67946-184">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="67946-185">Określanie użycia i stylu</span><span class="sxs-lookup"><span data-stu-id="67946-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="67946-186">Podczas opisywania usług przy użyciu Web Services Description Language (WSDL) dwa powszechnie używane style to dokumenty i zdalne wywoływanie procedur (RPC).</span><span class="sxs-lookup"><span data-stu-id="67946-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="67946-187">W stylu dokumentu cała treść komunikatu jest opisana przy użyciu schematu, a WSDL opisuje różne części treści komunikatów, odwołując się do elementów w tym schemacie.</span><span class="sxs-lookup"><span data-stu-id="67946-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="67946-188">W stylu RPC, WSDL odwołuje się do typu schematu dla każdej części wiadomości zamiast elementu.</span><span class="sxs-lookup"><span data-stu-id="67946-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="67946-189">W niektórych przypadkach trzeba ręcznie wybrać jeden z tych stylów.</span><span class="sxs-lookup"><span data-stu-id="67946-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="67946-190">Można to zrobić, stosując <xref:System.ServiceModel.DataContractFormatAttribute> atrybut i ustawiając `Style` Właściwość (gdy <xref:System.Runtime.Serialization.DataContractSerializer> jest używana) lub ustawiając `Style` <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybut (w przypadku używania <xref:System.Xml.Serialization.XmlSerializer> ).</span><span class="sxs-lookup"><span data-stu-id="67946-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="67946-191">Ponadto program <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwie formy serializowanych danych XML: `Literal` i `Encoded` .</span><span class="sxs-lookup"><span data-stu-id="67946-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="67946-192">`Literal`jest to najczęściej zaakceptowany formularz i jest jedynym formularzem <xref:System.Runtime.Serialization.DataContractSerializer> obsługiwanym przez program.</span><span class="sxs-lookup"><span data-stu-id="67946-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="67946-193">`Encoded`jest starszym formularzem opisanym w sekcji 5 specyfikacji protokołu SOAP i nie jest zalecany w przypadku nowych usług.</span><span class="sxs-lookup"><span data-stu-id="67946-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="67946-194">Aby przełączyć do `Encoded` trybu, należy ustawić `Use` właściwość atrybutu na <xref:System.ServiceModel.XmlSerializerFormatAttribute> `Encoded` .</span><span class="sxs-lookup"><span data-stu-id="67946-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="67946-195">W większości przypadków nie należy zmieniać ustawień domyślnych `Style` `Use` właściwości i.</span><span class="sxs-lookup"><span data-stu-id="67946-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="67946-196">Kontrolowanie procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="67946-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="67946-197">Aby dostosować sposób serializacji danych, można wykonać kilka czynności.</span><span class="sxs-lookup"><span data-stu-id="67946-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="67946-198">Zmienianie ustawień serializacji serwera</span><span class="sxs-lookup"><span data-stu-id="67946-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="67946-199">Gdy wartość domyślna <xref:System.Runtime.Serialization.DataContractSerializer> jest używana, można kontrolować pewne aspekty procesu serializacji w usłudze, stosując <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybut do usługi.</span><span class="sxs-lookup"><span data-stu-id="67946-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="67946-200">W `MaxItemsInObjectGraph` celu ustawienia limitu przydziału, który ogranicza maksymalną liczbę obiektów deserializacji, można użyć właściwości <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="67946-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="67946-201">Możesz użyć właściwości, `IgnoreExtensionDataObject` Aby wyłączyć funkcję zaokrąglania wersji.</span><span class="sxs-lookup"><span data-stu-id="67946-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="67946-202">Aby uzyskać więcej informacji na temat przydziałów, zobacz [zagadnienia dotyczące zabezpieczeń danych](security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="67946-202">For more information about quotas, see [Security Considerations for Data](security-considerations-for-data.md).</span></span> <span data-ttu-id="67946-203">Aby uzyskać więcej informacji na temat rundy, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="67946-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="67946-204">Zachowania serializacji</span><span class="sxs-lookup"><span data-stu-id="67946-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="67946-205">W programie WCF dostępne są dwa zachowania, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> które są automatycznie zasilane w zależności od tego, który serializator jest używany dla danej operacji.</span><span class="sxs-lookup"><span data-stu-id="67946-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="67946-206">Ponieważ te zachowania są stosowane automatycznie, zazwyczaj nie trzeba ich znać.</span><span class="sxs-lookup"><span data-stu-id="67946-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="67946-207">Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph` właściwości, i, `IgnoreExtensionDataObject` `DataContractSurrogate` których można użyć do dostosowania procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="67946-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="67946-208">Pierwsze dwie właściwości mają takie samo znaczenie jak omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="67946-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="67946-209">Możesz użyć `DataContractSurrogate` właściwości, aby włączyć surogaty kontraktu danych, który jest zaawansowanym mechanizmem do dostosowywania i rozszerzania procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="67946-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="67946-210">Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="67946-210">For more information, see [Data Contract Surrogates](../extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="67946-211">Można użyć, `DataContractSerializerOperationBehavior` Aby dostosować serializację klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="67946-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="67946-212">Poniższy przykład pokazuje, jak zwiększyć `MaxItemsInObjectGraph` przydział na kliencie.</span><span class="sxs-lookup"><span data-stu-id="67946-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="67946-213">Poniżej znajduje się odpowiedni kod w usłudze w przypadku samodzielnego udostępniania:</span><span class="sxs-lookup"><span data-stu-id="67946-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="67946-214">W przypadku przypadków hostowanych w sieci Web należy utworzyć nową `ServiceHost` klasę pochodną i użyć fabryki hosta usługi, aby ją podłączyć.</span><span class="sxs-lookup"><span data-stu-id="67946-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="67946-215">Kontrolowanie ustawień serializacji w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="67946-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="67946-216">`MaxItemsInObjectGraph`I `IgnoreExtensionDataObject` można ją kontrolować za pomocą konfiguracji przy użyciu `dataContractSerializer` punktu końcowego lub zachowania usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="67946-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="67946-217">Serializacja typu udostępnionego, zachowywania grafu obiektów i serializatorów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="67946-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="67946-218"><xref:System.Runtime.Serialization.DataContractSerializer>Serializacji używające nazw kontraktów danych, a nie nazw typów .NET.</span><span class="sxs-lookup"><span data-stu-id="67946-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="67946-219">Jest to zgodne z architekturą zorientowaną na usługę założenia i umożliwia zapewnienie doskonałej elastyczności — typy .NET mogą ulec zmianie bez wpływu na umowę sieciową.</span><span class="sxs-lookup"><span data-stu-id="67946-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="67946-220">W rzadkich przypadkach możesz chcieć serializować rzeczywiste nazwy typu .NET, co wprowadza ścisłe sprzężenie między klientem a serwerem, podobnie jak technologia komunikacji zdalnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67946-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="67946-221">Nie jest to zalecane rozwiązanie, z wyjątkiem rzadkich przypadków, które zazwyczaj występują podczas migracji do programu WCF z .NET Framework komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="67946-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="67946-222">W takim przypadku należy użyć <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="67946-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="67946-223"><xref:System.Runtime.Serialization.DataContractSerializer>Zwykle wykonuje serializacji grafów obiektów jako drzewa obiektów.</span><span class="sxs-lookup"><span data-stu-id="67946-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="67946-224">Oznacza to, że jeśli ten sam obiekt jest odwołuje się więcej niż raz, jest serializowany więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="67946-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="67946-225">Rozważmy na przykład `PurchaseOrder` wystąpienie mające dwa pola typu Address o nazwie `billTo` i `shipTo` .</span><span class="sxs-lookup"><span data-stu-id="67946-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="67946-226">Jeśli oba pola są ustawione na to samo wystąpienie adresu, istnieją dwa identyczne wystąpienia adresów po serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="67946-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="67946-227">Jest to realizowane z powodu braku interoperacyjności standardowej do reprezentowania grafów obiektów w kodzie XML (z wyjątkiem starszej wersji protokołu SOAP, która jest dostępna w systemie <xref:System.Xml.Serialization.XmlSerializer> , zgodnie z opisem w poprzedniej sekcji w systemach `Style` i `Use` ).</span><span class="sxs-lookup"><span data-stu-id="67946-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="67946-228">Serializacja grafów obiektów jako drzew ma pewne wady, na przykład wykresy z odwołaniami cyklicznymi nie mogą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="67946-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="67946-229">Czasami konieczne jest przełączenie na prawdziwą Serializacja grafu obiektów, nawet jeśli nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="67946-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="67946-230">Można to zrobić przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> konstrukcji z `preserveObjectReferences` parametrem ustawionym na `true` .</span><span class="sxs-lookup"><span data-stu-id="67946-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="67946-231">Czasami wbudowane serializatory są niewystarczające dla Twojego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="67946-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="67946-232">W większości przypadków można nadal używać <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakcji, z której zarówno, <xref:System.Runtime.Serialization.DataContractSerializer> jak i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodne.</span><span class="sxs-lookup"><span data-stu-id="67946-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="67946-233">W poprzednich trzech przypadkach (zachowywanie typu .NET, zachowywanie grafu obiektów i całkowicie niestandardowa `XmlObjectSerializer` Serializacja) wszystkie wymagają, aby niestandardowa serializator był podłączony.</span><span class="sxs-lookup"><span data-stu-id="67946-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="67946-234">W tym celu wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="67946-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="67946-235">Napisz własne zachowanie wynikające z programu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="67946-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="67946-236">Zastąp dwie `CreateSerializer` metody, aby zwrócić swój własny serializator ( <xref:System.Runtime.Serialization.NetDataContractSerializer> , <xref:System.Runtime.Serialization.DataContractSerializer> z opcją with `preserveObjectReferences` `true` lub własny niestandardowy <xref:System.Runtime.Serialization.XmlObjectSerializer> ).</span><span class="sxs-lookup"><span data-stu-id="67946-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="67946-237">Przed otwarciem hosta usługi lub utworzeniem kanału klienta należy usunąć istniejące <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zachowanie i podłączyć niestandardową klasę pochodną utworzoną w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="67946-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="67946-238">Aby uzyskać więcej informacji na temat zaawansowanych koncepcji serializacji, zobacz [serializacji i deserializacji](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="67946-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67946-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67946-239">See also</span></span>

- [<span data-ttu-id="67946-240">Używanie klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="67946-240">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)
- [<span data-ttu-id="67946-241">Instrukcje: włączanie przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="67946-241">How to: Enable Streaming</span></span>](how-to-enable-streaming.md)
- [<span data-ttu-id="67946-242">Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="67946-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
