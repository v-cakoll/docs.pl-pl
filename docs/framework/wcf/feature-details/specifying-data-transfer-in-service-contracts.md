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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748151"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="836e6-102">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="836e6-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="836e6-103">Windows Communication Foundation (WCF) mogą być uważane za to infrastruktura obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="836e6-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="836e6-104">Operacje usługi można odbierać komunikaty, przetwarzać je i wysyłania im komunikatów.</span><span class="sxs-lookup"><span data-stu-id="836e6-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="836e6-105">Komunikaty są opisane za pomocą kontrakty operacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="836e6-106">Na przykład należy wziąć pod uwagę następujące umowy.</span><span class="sxs-lookup"><span data-stu-id="836e6-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="836e6-107">W tym miejscu `GetAirfare` operacji akceptuje komunikat z informacjami o `fromCity` i `toCity`, a następnie zwraca komunikat, który zawiera numer.</span><span class="sxs-lookup"><span data-stu-id="836e6-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="836e6-108">W tym temacie opisano różne sposoby, w których kontrakt operacji można opisać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="836e6-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="836e6-109">Opisujące wiadomości przy użyciu parametrów</span><span class="sxs-lookup"><span data-stu-id="836e6-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="836e6-110">Najprostszym sposobem opisują wiadomość jest listą parametrów i wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="836e6-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="836e6-111">W powyższym przykładzie `fromCity` i `toCity` parametry były używane do opisywania komunikat żądania, a wartość zwracaną float został użyty do opisania komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="836e6-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="836e6-112">Jeśli samodzielnie wartość zwracana nie jest wystarczająco dużo, aby opisać komunikat odpowiedzi, parametry wyjściowe mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="836e6-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="836e6-113">Na przykład następująca operacja ma `fromCity` i `toCity` w jego komunikat żądania oraz numer wraz z waluty w jego komunikat odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="836e6-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="836e6-114">Ponadto można używać parametrów odwołania do parametru częścią zarówno żądanie, jak i komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="836e6-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="836e6-115">Parametry muszą być typów, które można wykonywać serializację (przekonwertować na format XML).</span><span class="sxs-lookup"><span data-stu-id="836e6-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="836e6-116">Domyślnie program WCF używa składnik o nazwie <xref:System.Runtime.Serialization.DataContractSerializer> klasy, aby wykonać tę konwersję.</span><span class="sxs-lookup"><span data-stu-id="836e6-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="836e6-117">Typy pierwotne najbardziej (takie jak `int`, `string`, `float`, i `DateTime`.) są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="836e6-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="836e6-118">Typy zdefiniowane przez użytkownika musi mieć zwykle kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="836e6-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="836e6-119">Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="836e6-120">Od czasu do czasu `DataContractSerializer` nie jest odpowiednia do serializacji typów.</span><span class="sxs-lookup"><span data-stu-id="836e6-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="836e6-121">Usługi WCF obsługuje mechanizm serializacji alternatywne, <xref:System.Xml.Serialization.XmlSerializer>, który umożliwia także serializować parametrów.</span><span class="sxs-lookup"><span data-stu-id="836e6-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="836e6-122"><xref:System.Xml.Serialization.XmlSerializer> Umożliwia większą kontrolę nad wynikowy kod XML przy użyciu atrybutów, takich jak `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="836e6-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="836e6-123">Aby przełączyć się do korzystania z <xref:System.Xml.Serialization.XmlSerializer> dla określonej operacji lub dla całej usługi naliczone <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu do operacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="836e6-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="836e6-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="836e6-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="836e6-125">Aby uzyskać więcej informacji, zobacz [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="836e6-126">Należy pamiętać, że ręczne przełączanie do <xref:System.Xml.Serialization.XmlSerializer> jak pokazano w tym miejscu nie jest zalecane, chyba że masz powody, aby zrobić tak jak wyjaśniono w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="836e6-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="836e6-127">Aby wyizolować .NET nazwy parametru od nazw kontraktu, można użyć <xref:System.ServiceModel.MessageParameterAttribute> atrybutu, a następnie użyj `Name` właściwość można ustawić nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="836e6-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="836e6-128">Na przykład następujące kontrakt operacji jest równoważne z pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="836e6-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="836e6-129">Opisujące pusty wiadomości</span><span class="sxs-lookup"><span data-stu-id="836e6-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="836e6-130">Komunikat żądania pustą można opisać za pomocą o bez parametrów danych wejściowych lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="836e6-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="836e6-131">Na przykład w C#:</span><span class="sxs-lookup"><span data-stu-id="836e6-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="836e6-132">Na przykład w języku VB:</span><span class="sxs-lookup"><span data-stu-id="836e6-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="836e6-133">Komunikat odpowiedzi pusty można opisać za pomocą o `void` zwracać typ i bez parametrów danych wyjściowych lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="836e6-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="836e6-134">Na przykład w:</span><span class="sxs-lookup"><span data-stu-id="836e6-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="836e6-135">To różni się od operacji jednokierunkowych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="836e6-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="836e6-136">`SetTemperatureStatus` Operacja zwraca pusty komunikat.</span><span class="sxs-lookup"><span data-stu-id="836e6-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="836e6-137">Jego może zwracać błędów zamiast Jeśli występuje problem podczas przetwarzania komunikatu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="836e6-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="836e6-138">`SetLightbulbStatus` Operacji nie zwraca żadnego.</span><span class="sxs-lookup"><span data-stu-id="836e6-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="836e6-139">Nie ma możliwości do komunikowania się warunek błędu z tej operacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="836e6-140">Opisujące komunikatów za pomocą kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="836e6-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="836e6-141">Można użyć jednego typu do reprezentowania cały komunikat.</span><span class="sxs-lookup"><span data-stu-id="836e6-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="836e6-142">Chociaż jest możliwe użycie kontraktu danych, w tym celu, zalecanym sposobem na to jest użycie kontraktu komunikatu — pozwala to uniknąć niepotrzebnych poziomy zawijania wynikowego pliku XML.</span><span class="sxs-lookup"><span data-stu-id="836e6-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="836e6-143">Kontrakty komunikatów umożliwiają ponadto większa kontrola nad wynikowe wiadomości.</span><span class="sxs-lookup"><span data-stu-id="836e6-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="836e6-144">Na przykład można zdecydować, informacje powinien znajdować się w treści komunikatu i powinien być w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="836e6-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="836e6-145">Używanie kontraktów komunikatu można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="836e6-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="836e6-146">Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="836e6-147">W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> klasy jest nadal używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="836e6-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="836e6-148"><xref:System.Xml.Serialization.XmlSerializer> Klasy można również za pomocą kontraktów komunikatu.</span><span class="sxs-lookup"><span data-stu-id="836e6-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="836e6-149">Aby to zrobić, należy zastosować <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu do operacji lub umowy i używanie typów zgodnych z <xref:System.Xml.Serialization.XmlSerializer> klasy w nagłówki komunikatów i elementów członkowskich jednostki.</span><span class="sxs-lookup"><span data-stu-id="836e6-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="836e6-150">Opisujące komunikatów za pomocą strumieni</span><span class="sxs-lookup"><span data-stu-id="836e6-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="836e6-151">Opisują komunikaty w operacjach na innym sposobem jest użycie <xref:System.IO.Stream> klasy lub jednej z jej klas pochodnych w kontrakt operacji lub jako członek treści kontraktu komunikatu (musi mieć wartość tylko element członkowski w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="836e6-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="836e6-152">Dla wiadomości przychodzących, musi być typu `Stream`— nie można użyć klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="836e6-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="836e6-153">Zamiast wywoływania serializator, WCF pobiera dane ze strumienia i umieszcza go bezpośrednio do wysyłanej wiadomości lub pobiera dane z wiadomości przychodzących i umieszcza go bezpośrednio do strumienia.</span><span class="sxs-lookup"><span data-stu-id="836e6-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="836e6-154">Poniższy przykład pokazuje użycie strumieni.</span><span class="sxs-lookup"><span data-stu-id="836e6-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="836e6-155">Nie można łączyć `Stream` i Transmituj — w treści pojedynczym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="836e6-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="836e6-156">Użyj kontraktu komunikatu, aby umieścić dodatkowe dane w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="836e6-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="836e6-157">Poniższy kod przedstawia nieprawidłowe użycie strumieni podczas definiowania kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="836e6-158">Poniższy przykład pokazuje poprawne użycie strumieni podczas definiowania kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="836e6-159">Aby uzyskać więcej informacji, zobacz [duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="836e6-160">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="836e6-160">Using the Message Class</span></span>  
 <span data-ttu-id="836e6-161">Aby mieć pełną kontrolę programowy za pośrednictwem wiadomości wysyłane lub odbierane, można użyć <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="836e6-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="836e6-162">Jest to zaawansowany scenariusz, opisana szczegółowo w temacie [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="836e6-163">Opisujące komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="836e6-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="836e6-164">Oprócz wiadomości, które są opisane przez wartość zwracaną i parametry danych wyjściowych lub odwołania, każdej operacji, która nie jest jednokierunkowa może zwrócić co najmniej dwa możliwe komunikaty: komunikat odpowiedzi normalne i komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="836e6-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="836e6-165">Należy wziąć pod uwagę następujące kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="836e6-166">Ta operacja albo może zwracać normalny komunikat dotyczący, który zawiera `float` numer lub komunikat o błędzie, który zawiera kod błędu i opis.</span><span class="sxs-lookup"><span data-stu-id="836e6-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="836e6-167">Można to zrobić, zwracając <xref:System.ServiceModel.FaultException> w danej implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="836e6-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="836e6-168">Komunikaty dodatkowych możliwych błędów można określić za pomocą <xref:System.ServiceModel.FaultContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="836e6-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="836e6-169">Dodatkowe błędy musi być możliwy do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="836e6-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="836e6-170">Te dodatkowe błędy mogą być generowane przez zgłaszanie <xref:System.ServiceModel.FaultException%601> typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="836e6-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="836e6-171">Aby uzyskać więcej informacji, zobacz [obsługi wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="836e6-172">Nie można użyć <xref:System.Xml.Serialization.XmlSerializer> klasę do opisania błędów.</span><span class="sxs-lookup"><span data-stu-id="836e6-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="836e6-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Nie ma wpływu na kontraktów błędów.</span><span class="sxs-lookup"><span data-stu-id="836e6-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="836e6-174">Przy użyciu typów pochodnych</span><span class="sxs-lookup"><span data-stu-id="836e6-174">Using Derived Types</span></span>  
 <span data-ttu-id="836e6-175">Można użyć typu podstawowego w operacji lub kontraktu komunikatu, a następnie użyj typu pochodnego, podczas wywoływania faktycznie wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="836e6-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="836e6-176">W takim przypadku należy użyć <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub niektóre alternatywny mechanizm umożliwiający korzystanie z typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="836e6-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="836e6-177">Należy wziąć pod uwagę następujące działania.</span><span class="sxs-lookup"><span data-stu-id="836e6-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="836e6-178">Przyjęto założenie, że dwa typy `Book` i `Magazine`, pochodzi od `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="836e6-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="836e6-179">Używanie tych typów w `IsLibraryItemAvailable` operacji, można zmienić operacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="836e6-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="836e6-180">Alternatywnie, można użyć <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu, gdy domyślny <xref:System.Runtime.Serialization.DataContractSerializer> jest w użyciu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="836e6-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="836e6-181">Możesz użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="836e6-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="836e6-182">Można zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutów, operacji lub całą usługę.</span><span class="sxs-lookup"><span data-stu-id="836e6-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="836e6-183">Przyjmuje typ albo nazwa metody do wywołania w celu uzyskania listy znanych typów, podobnie jak <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="836e6-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="836e6-184">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="836e6-185">Określanie Use i Style</span><span class="sxs-lookup"><span data-stu-id="836e6-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="836e6-186">W opisie usług za pomocą sieci Web Services Description Language (WSDL), dwa najczęściej używane style są dokument i zdalnego wywołania procedury (RPC).</span><span class="sxs-lookup"><span data-stu-id="836e6-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="836e6-187">W stylu dokumentu opisano treści cały komunikat przy użyciu schematu i WSDL w tym artykule opisano różne części treści wiadomości, odwołując się do elementów w tym schemacie.</span><span class="sxs-lookup"><span data-stu-id="836e6-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="836e6-188">W stylu RPC WSDL odwołuje się do typu schematu dla każdej części komunikatu zamiast elementu.</span><span class="sxs-lookup"><span data-stu-id="836e6-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="836e6-189">W niektórych przypadkach trzeba ręcznie wybrać jeden z tych stylów.</span><span class="sxs-lookup"><span data-stu-id="836e6-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="836e6-190">Można to robić przez zastosowanie <xref:System.ServiceModel.DataContractFormatAttribute> atrybutów i ustawienie `Style` właściwości (po <xref:System.Runtime.Serialization.DataContractSerializer> jest używany), lub poprzez skonfigurowanie `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu (korzystając z <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="836e6-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="836e6-191">Ponadto <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwa rodzaje serializacji XML: `Literal` i `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="836e6-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="836e6-192">`Literal` to najbardziej powszechnie akceptowane formularza i jest tylko formularz <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje.</span><span class="sxs-lookup"><span data-stu-id="836e6-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="836e6-193">`Encoded` jest formą starszych opisane w sekcji 5 specyfikacji protokołu SOAP, a nie jest zalecane w przypadku nowych usług.</span><span class="sxs-lookup"><span data-stu-id="836e6-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="836e6-194">Aby przełączyć się do `Encoded` ustawiony tryb, `Use` właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="836e6-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="836e6-195">W większości przypadków nie należy zmieniać domyślne ustawienia dla `Style` i `Use` właściwości.</span><span class="sxs-lookup"><span data-stu-id="836e6-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="836e6-196">Sterowanie procesem serializacji</span><span class="sxs-lookup"><span data-stu-id="836e6-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="836e6-197">Można zrobić kilka rzeczy, aby dostosować sposób, w jaki dane jest serializowana.</span><span class="sxs-lookup"><span data-stu-id="836e6-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="836e6-198">Zmienianie ustawień serializacji serwera</span><span class="sxs-lookup"><span data-stu-id="836e6-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="836e6-199">Gdy domyślne <xref:System.Runtime.Serialization.DataContractSerializer> jest używany, można kontrolować niektóre aspekty procesu serializacji w usłudze, stosując <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu w usłudze.</span><span class="sxs-lookup"><span data-stu-id="836e6-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="836e6-200">W szczególności można użyć `MaxItemsInObjectGraph` właściwość umożliwiająca ustawienie limitu przydziału, która ogranicza maksymalną liczbę obiektów <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje.</span><span class="sxs-lookup"><span data-stu-id="836e6-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="836e6-201">Możesz użyć `IgnoreExtensionDataObject` właściwości, aby wyłączyć funkcji przechowywania wersji Pełna zgodnooć wersji.</span><span class="sxs-lookup"><span data-stu-id="836e6-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="836e6-202">Aby uzyskać więcej informacji na temat limitów przydziału, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="836e6-203">Aby uzyskać więcej informacji na temat Pełna zgodnooć wersji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="836e6-204">Zachowania serializacji</span><span class="sxs-lookup"><span data-stu-id="836e6-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="836e6-205">Dwa zachowania są dostępne w programie WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , automatycznie są podłączone w zależności od którego serializator jest używany dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="836e6-206">Ponieważ te zachowania są stosowane automatycznie, zwykle nie trzeba się z nimi zapoznać.</span><span class="sxs-lookup"><span data-stu-id="836e6-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="836e6-207">Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, i `DataContractSurrogate` właściwości, które umożliwiają dostosowanie procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="836e6-208">Pierwsze dwie właściwości mają takie samo znaczenie, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="836e6-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="836e6-209">Możesz użyć `DataContractSurrogate` właściwością pozwalającą włączyć surogaty kontraktu danych, które zaawansowany mechanizm dostosowywanie i rozszerzanie procesem serializacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="836e6-210">Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="836e6-211">Możesz użyć `DataContractSerializerOperationBehavior` dostosować serializacji klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="836e6-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="836e6-212">Poniższy przykład pokazuje, jak zwiększyć `MaxItemsInObjectGraph` limitu przydziału na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="836e6-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
 <span data-ttu-id="836e6-213">Poniżej przedstawiono równoważny kod w tym przypadku samodzielnie hostowanej usłudze.</span><span class="sxs-lookup"><span data-stu-id="836e6-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
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
  
 <span data-ttu-id="836e6-214">W przypadku hostowanych w sieci Web, należy utworzyć nowy `ServiceHost` klasy pochodnej, a następnie dołączyć go za pomocą fabryki hostów usług.</span><span class="sxs-lookup"><span data-stu-id="836e6-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="836e6-215">Kontrolowanie serializacji ustawień konfiguracji</span><span class="sxs-lookup"><span data-stu-id="836e6-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="836e6-216">`MaxItemsInObjectGraph` i `IgnoreExtensionDataObject` mogą być kontrolowane za pośrednictwem konfiguracji za pomocą `dataContractSerializer` zachowanie punktu końcowego lub usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="836e6-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="836e6-217">Udostępniony serializacja typów, zachowywania wykresu obiektu i serializatorów niestandardowe</span><span class="sxs-lookup"><span data-stu-id="836e6-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="836e6-218"><xref:System.Runtime.Serialization.DataContractSerializer> Serializuje przy użyciu nazwy kontraktów danych i nie nazwy typów .NET.</span><span class="sxs-lookup"><span data-stu-id="836e6-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="836e6-219">To jest spójna z założenia architektury zorientowanej na usługi i umożliwia precyzyjną elastyczność — typy .NET można zmienić bez wpływu na kontrakt o komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="836e6-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="836e6-220">W rzadkich przypadkach można serializować rzeczywiste nazwy typu .NET, a tym samym Przedstawiamy ścisłego sprzężenia między klientem a serwerem, podobne do technologii wywołaniem funkcji zdalnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="836e6-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="836e6-221">To nie jest zalecana praktyka, z wyjątkiem w rzadkich przypadkach, zwykle występujących podczas migracji do programu WCF z wywołaniem funkcji zdalnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="836e6-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="836e6-222">W takim przypadku należy użyć <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="836e6-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="836e6-223"><xref:System.Runtime.Serialization.DataContractSerializer> Zwykle serializuje wykresów obiektów jako drzewa obiektów.</span><span class="sxs-lookup"><span data-stu-id="836e6-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="836e6-224">Oznacza to jeżeli ten sam obiekt jest określona więcej niż jeden raz, jest serializowana więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="836e6-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="836e6-225">Na przykład, rozważmy `PurchaseOrder` wystąpienia, która ma dwa pola typu adres o nazwie `billTo` i `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="836e6-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="836e6-226">Jeśli oba pola są ustawione na tym samym wystąpieniu adres, istnieją dwa identyczne wystąpienia adres po serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="836e6-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="836e6-227">Odbywa się, ponieważ nie istnieje żadne standardowy sposób interoperacyjny do reprezentowania wykresów obiektów w formacie XML (z wyjątkiem dostępne w starszej wersji standard protokołu SOAP zakodowane <xref:System.Xml.Serialization.XmlSerializer>, zgodnie z opisem w poprzedniej sekcji na `Style` i `Use`).</span><span class="sxs-lookup"><span data-stu-id="836e6-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="836e6-228">Serializowanie wykresów obiektów jako drzewa ma pewne wady, na przykład wykresów z odwołania cykliczne nie może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="836e6-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="836e6-229">Od czasu do czasu jest niezbędne przełączyć się do serializacji grafu obiektów wartość true, mimo że nie ma międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="836e6-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="836e6-230">Można to zrobić za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> skonstruowany przy użyciu `preserveObjectReferences` parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="836e6-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="836e6-231">Od czasu do czasu wbudowane serializatory nie są wystarczające dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="836e6-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="836e6-232">W większości przypadków można nadal używać <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakcji, z których obie <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodnych.</span><span class="sxs-lookup"><span data-stu-id="836e6-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="836e6-233">Poprzednie trzy przypadki (zachowywanie typu .NET, konserwowania wykresu obiektu i całkowicie niestandardowe `XmlObjectSerializer`— na podstawie serializacji) wymaga niestandardowy serializator są podłączone.</span><span class="sxs-lookup"><span data-stu-id="836e6-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="836e6-234">W tym celu wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="836e6-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="836e6-235">Napisać własne zachowanie wynikające z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="836e6-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="836e6-236">Zastąp dwa `CreateSerializer` metody zwracają własne serializatora (albo <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> z `preserveObjectReferences` równa `true`, lub własne niestandardowe <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="836e6-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="836e6-237">Przed otwarciem hosta usługi lub tworzenia kanału klienta, Usuń istniejące <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zachowanie i wtyczki niestandardowe klasy pochodnej, który został utworzony w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="836e6-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="836e6-238">Aby uzyskać więcej informacji o pojęciach dotyczących zaawansowanych serializacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="836e6-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="836e6-239">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="836e6-239">See also</span></span>

- [<span data-ttu-id="836e6-240">Używanie klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="836e6-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="836e6-241">Instrukcje: Włączanie przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="836e6-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="836e6-242">Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="836e6-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
