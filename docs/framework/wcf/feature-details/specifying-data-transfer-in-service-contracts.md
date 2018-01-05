---
title: "Określanie transferu danych w kontraktach usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c650a59402099e1fe71a0292dd0ccfc409d3448d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="f7889-102">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="f7889-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="f7889-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Można traktować jako infrastruktury obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="f7889-104">Operacje usługi można odbierać wiadomości, ich przetworzyć i wysyłanie do nich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="f7889-105">Komunikaty są opisane przy użyciu kontrakty operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="f7889-106">Na przykład należy wziąć pod uwagę następujące kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f7889-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="f7889-107">W tym miejscu `GetAirfare` operacji akceptuje komunikat z informacjami o `fromCity` i `toCity`, a następnie zwraca komunikat, który zawiera liczbę.</span><span class="sxs-lookup"><span data-stu-id="f7889-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="f7889-108">W tym temacie opisano różne sposoby, w których kontrakt operacji można opisać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="f7889-109">Opisujące wiadomości przy użyciu parametrów</span><span class="sxs-lookup"><span data-stu-id="f7889-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="f7889-110">Najprostszym sposobem, aby opisać wiadomość jest użycie listy parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="f7889-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="f7889-111">W powyższym przykładzie `fromCity` i `toCity` parametrów ciągu były używane do opisywania komunikat żądania, a wartością zwracaną typu float zostało użyte do opisu komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f7889-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="f7889-112">Jeśli tylko wartości zwracanej nie jest wystarczająca do opisywania komunikat odpowiedzi, parametrów out może być używany.</span><span class="sxs-lookup"><span data-stu-id="f7889-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="f7889-113">Na przykład następująca operacja ma `fromCity` i `toCity` komunikatu żądania i numer wraz z waluty w jego komunikat odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="f7889-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="f7889-114">Ponadto można używać parametrów odwołania do parametru część zarówno żądanie, jak i komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f7889-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="f7889-115">Parametry muszą być typów, które można serializować (przekonwertowane na format XML).</span><span class="sxs-lookup"><span data-stu-id="f7889-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="f7889-116">Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnikiem o nazwie <xref:System.Runtime.Serialization.DataContractSerializer> klasy do wykonania konwersji.</span><span class="sxs-lookup"><span data-stu-id="f7889-116">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="f7889-117">Typy pierwotne najbardziej (takich jak `int`, `string`, `float`, i `DateTime`.) są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f7889-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="f7889-118">Typy definiowane przez użytkownika musi mieć zwykle kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f7889-118">User-defined types must normally have a data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-119">[Za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-119"> [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="f7889-120">Czasami `DataContractSerializer` nie jest odpowiednia do serializacji typów sieci.</span><span class="sxs-lookup"><span data-stu-id="f7889-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f7889-121">obsługuje mechanizm alternatywny serializacji, <xref:System.Xml.Serialization.XmlSerializer>, który można serializować parametrów.</span><span class="sxs-lookup"><span data-stu-id="f7889-121"> supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="f7889-122"><xref:System.Xml.Serialization.XmlSerializer> Umożliwia użycie większą kontrolę nad wynikowego pliku XML przy użyciu atrybutów, takich jak `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f7889-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="f7889-123">Aby przełączyć się do przy użyciu <xref:System.Xml.Serialization.XmlSerializer> mają zastosowanie dla określonej operacji lub dla całej usługi <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu w celu wykonania operacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="f7889-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="f7889-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f7889-124">For example:</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-125">[Przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-125"> [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="f7889-126">Należy pamiętać, że ręczne przełączanie do <xref:System.Xml.Serialization.XmlSerializer> opisane w tym miejscu nie jest zalecane, chyba że masz właściwe przyczyny robić, tak jak szczegółowe, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f7889-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="f7889-127">Aby wyizolować .NET nazwy parametru od nazw kontraktu, można użyć <xref:System.ServiceModel.MessageParameterAttribute> atrybutu, a następnie użyj `Name` właściwości można ustawić nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f7889-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="f7889-128">Na przykład następujące kontrakt operacji jest odpowiednikiem pierwszym przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f7889-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="f7889-129">Opisujące pusty wiadomości</span><span class="sxs-lookup"><span data-stu-id="f7889-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="f7889-130">Komunikat żądania pusty można opisać za pomocą o bez parametrów wejściowych lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f7889-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="f7889-131">Na przykład w języku C#:</span><span class="sxs-lookup"><span data-stu-id="f7889-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="f7889-132">Na przykład w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="f7889-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="f7889-133">Komunikat odpowiedzi pusty można opisać za pomocą o `void` zwracany typ i bez parametrów wyjściowych lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f7889-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="f7889-134">Na przykład w:</span><span class="sxs-lookup"><span data-stu-id="f7889-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="f7889-135">Różni się to od operacji jednokierunkowych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="f7889-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="f7889-136">`SetTemperatureStatus` Operacja zwraca komunikat puste.</span><span class="sxs-lookup"><span data-stu-id="f7889-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="f7889-137">Go mogą zwracać błąd zamiast tego przypadku problem podczas przetwarzania komunikatu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="f7889-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="f7889-138">`SetLightbulbStatus` Operacji nie zwraca żadnego.</span><span class="sxs-lookup"><span data-stu-id="f7889-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="f7889-139">Nie istnieje sposób do komunikowania się warunek błędu z tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="f7889-140">Opisujące wiadomości za pomocą kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="f7889-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="f7889-141">Można użyć jednego typu do reprezentowania cały komunikat.</span><span class="sxs-lookup"><span data-stu-id="f7889-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="f7889-142">Jest możliwe użycie kontraktu danych do tego celu, w tym zalecaną metodą jest użycie kontraktu komunikatu — dzięki temu można uniknąć niepotrzebnych poziomów zawijania wynikowe dane XML.</span><span class="sxs-lookup"><span data-stu-id="f7889-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="f7889-143">Ponadto kontraktów komunikatu umożliwiają większej kontroli nad wynikowe wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="f7889-144">Na przykład można zdecydować, informacje powinna być w treści wiadomości i powinny być w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="f7889-145">Poniższy przykład przedstawia użycie kontraktów komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f7889-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-146">[Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-146"> [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="f7889-147">W poprzednim przykładzie <xref:System.Runtime.Serialization.DataContractSerializer> klasy jest wciąż używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f7889-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="f7889-148"><xref:System.Xml.Serialization.XmlSerializer> Klasa może być używana również z kontraktów komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f7889-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="f7889-149">Aby to zrobić, należy zastosować <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu w celu wykonania operacji lub kontrakt i używanie typów zgodne z <xref:System.Xml.Serialization.XmlSerializer> klasy w nagłówkach wiadomości i członków treści.</span><span class="sxs-lookup"><span data-stu-id="f7889-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="f7889-150">Opisujące wiadomości przy użyciu strumieni</span><span class="sxs-lookup"><span data-stu-id="f7889-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="f7889-151">Innym sposobem opisują komunikaty w operacji jest użycie <xref:System.IO.Stream> klasy lub jednej z jej klas pochodnych w kontrakt operacji lub jako członek treści kontraktu komunikatu (musi być jedynym członkiem w takim przypadku).</span><span class="sxs-lookup"><span data-stu-id="f7889-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="f7889-152">Dla komunikatów przychodzących, typ musi być `Stream`— nie można używać klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f7889-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="f7889-153">Zamiast wywoływania serializator, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pobiera dane ze strumienia i umieszcza je bezpośrednio do wiadomości wychodzącej lub pobiera dane z komunikatu przychodzącego i umieszcza je bezpośrednio do strumienia.</span><span class="sxs-lookup"><span data-stu-id="f7889-153">Instead of invoking the serializer, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="f7889-154">Poniższy przykład przedstawia korzystanie ze strumieni.</span><span class="sxs-lookup"><span data-stu-id="f7889-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="f7889-155">Nie można łączyć `Stream` i danych z systemem innym niż strumienia w treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="f7889-156">Użyj kontraktu komunikatu, aby umieścić dodatkowe dane w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7889-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="f7889-157">W poniższym przykładzie przedstawiono nieprawidłowe użycie strumieni podczas definiowania kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="f7889-158">Poniższy przykład przedstawia odpowiednie użycie strumieni podczas definiowania kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-159">[Dużej ilości danych i przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-159"> [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="f7889-160">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="f7889-160">Using the Message Class</span></span>  
 <span data-ttu-id="f7889-161">Aby mieć pełną kontrolę programowy za pośrednictwem wiadomości wysyłane lub odbierane, można użyć <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7889-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="f7889-162">Jest to bardziej zaawansowany scenariusz, który opisano szczegółowo w [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="f7889-163">Opisujące komunikatów "Fault"</span><span class="sxs-lookup"><span data-stu-id="f7889-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="f7889-164">Oprócz wiadomości, które są opisane w zwracanej wartości i parametrów wyjściowych lub odwołanie, żadnej operacji, która nie jest jednokierunkowa można zwrócić co najmniej dwa komunikaty możliwe: komunikatu odpowiedzi normalne i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f7889-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="f7889-165">Należy wziąć pod uwagę następujące kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="f7889-166">Ta operacja albo może zwracać normalne komunikat, który zawiera `float` numer lub komunikat o błędzie, który zawiera kod błędu i opis.</span><span class="sxs-lookup"><span data-stu-id="f7889-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="f7889-167">Można to zrobić przez zgłaszanie <xref:System.ServiceModel.FaultException> w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f7889-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="f7889-168">Można określić dodatkowe możliwych błędów wiadomości przy użyciu <xref:System.ServiceModel.FaultContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f7889-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="f7889-169">Dodatkowe błędy musi być możliwy do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7889-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="f7889-170">Te dodatkowe błędy mogą być generowane przez zgłaszanie <xref:System.ServiceModel.FaultException%601> typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f7889-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-171">[Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-171"> [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="f7889-172">Nie można użyć <xref:System.Xml.Serialization.XmlSerializer> klasy do opisywania błędów.</span><span class="sxs-lookup"><span data-stu-id="f7889-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="f7889-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Nie ma wpływu na kontrakty błędów.</span><span class="sxs-lookup"><span data-stu-id="f7889-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="f7889-174">Przy użyciu typów pochodnych</span><span class="sxs-lookup"><span data-stu-id="f7889-174">Using Derived Types</span></span>  
 <span data-ttu-id="f7889-175">Można użyć typu podstawowego w operacji lub kontraktu komunikatu, a następnie użyj typu pochodnego podczas faktycznie wywoływania operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="f7889-176">W takim przypadku należy użyć jednego <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu lub niektóre alternatywny mechanizm zezwala na używanie typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f7889-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="f7889-177">Należy rozważyć następujące działania.</span><span class="sxs-lookup"><span data-stu-id="f7889-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="f7889-178">Załóżmy, że dwa typy, `Book` i `Magazine`, pochodzi z `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="f7889-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="f7889-179">Używanie tych typów w `IsLibraryItemAvailable` operacji, można zmienić operację w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f7889-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="f7889-180">Alternatywnie można użyć <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu, gdy domyślny <xref:System.Runtime.Serialization.DataContractSerializer> jest w użyciu, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7889-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="f7889-181">Można użyć <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybutu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f7889-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="f7889-182">Możesz zastosować <xref:System.ServiceModel.ServiceKnownTypeAttribute> atrybutu operacji lub całej usługi.</span><span class="sxs-lookup"><span data-stu-id="f7889-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="f7889-183">Przyjmuje typ albo nazwa metody do wywołania w celu uzyskania listy znanych typów, podobnie jak <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f7889-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-184">[Znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-184"> [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="f7889-185">Określanie Use i Style</span><span class="sxs-lookup"><span data-stu-id="f7889-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="f7889-186">W opisie usług za pomocą sieci Web Services Description Language (WSDL), dwa najczęściej używane style są dokument i zdalnego wywołania procedury (RPC).</span><span class="sxs-lookup"><span data-stu-id="f7889-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="f7889-187">W stylu dokumentu opisano treści cały komunikat przy użyciu schematu i WSDL opisano różne części treści wiadomości, odwołując się do elementów w ramach tego schematu.</span><span class="sxs-lookup"><span data-stu-id="f7889-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="f7889-188">W stylu wywołania RPC WSDL odwołuje się do typu schematu dla każdej części komunikatu zamiast elementu.</span><span class="sxs-lookup"><span data-stu-id="f7889-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="f7889-189">W niektórych przypadkach należy ręcznie wybrać jeden z tych stylów.</span><span class="sxs-lookup"><span data-stu-id="f7889-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="f7889-190">Można to zrobić przez zastosowanie <xref:System.ServiceModel.DataContractFormatAttribute> atrybut i ustawienie `Style` właściwości (przy <xref:System.Runtime.Serialization.DataContractSerializer> jest używany), lub przez ustawienie `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu (przy użyciu <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="f7889-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="f7889-191">Ponadto <xref:System.Xml.Serialization.XmlSerializer> obsługuje dwa rodzaje serializacji XML: `Literal` i `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="f7889-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="f7889-192">`Literal`jest najczęściej zaakceptowane formularza i jest jedyną <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje.</span><span class="sxs-lookup"><span data-stu-id="f7889-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="f7889-193">`Encoded`jest formą starszych opisane w sekcji 5 specyfikacji protokołu SOAP, a nie jest zalecane w przypadku nowych usług.</span><span class="sxs-lookup"><span data-stu-id="f7889-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="f7889-194">Aby przełączyć się do `Encoded` tryb, `Use` właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute> atrybutu `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="f7889-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="f7889-195">W większości przypadków, nie należy zmieniać ustawienia domyślne dla `Style` i `Use` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7889-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="f7889-196">Kontrolowanie procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="f7889-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="f7889-197">Można zrobić na kilka rzeczy, które można dostosować sposób danych jest serializowany.</span><span class="sxs-lookup"><span data-stu-id="f7889-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="f7889-198">Zmiana ustawień serializacji serwera</span><span class="sxs-lookup"><span data-stu-id="f7889-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="f7889-199">Gdy domyślne <xref:System.Runtime.Serialization.DataContractSerializer> jest używana, można kontrolować niektóre aspekty procesu serializacji w usłudze, stosując <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu z usługą.</span><span class="sxs-lookup"><span data-stu-id="f7889-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="f7889-200">W szczególności mogą używać `MaxItemsInObjectGraph` właściwości można ustawić limit przydziału, która ogranicza maksymalną liczbę obiektów <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje.</span><span class="sxs-lookup"><span data-stu-id="f7889-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="f7889-201">Można użyć `IgnoreExtensionDataObject` właściwości, aby wyłączyć funkcji przechowywania wersji dwustronną komunikację.</span><span class="sxs-lookup"><span data-stu-id="f7889-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f7889-202">przydziały, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-202"> quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f7889-203">dwustronną komunikację, zobacz [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-203"> round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="f7889-204">Zachowania serializacji</span><span class="sxs-lookup"><span data-stu-id="f7889-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="f7889-205">Dostępne są dwa zachowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> który automatycznie są podłączone w zależności od którego serializator jest używana dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-205">Two behaviors are available in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="f7889-206">Ponieważ te zachowania są automatycznie stosowane, zwykle nie trzeba się z nimi zapoznać.</span><span class="sxs-lookup"><span data-stu-id="f7889-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="f7889-207">Jednak `DataContractSerializerOperationBehavior` ma `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, i `DataContractSurrogate` właściwości, których można użyć do dostosowania procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="f7889-208">Pierwsze dwie właściwości mają takie samo znaczenie, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f7889-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="f7889-209">Można użyć `DataContractSurrogate` właściwości, aby włączyć surogaty kontraktu danych, które są zaawansowany mechanizm dostosowywanie i rozszerzanie procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f7889-210">[Surogatów kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-210"> [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="f7889-211">Można użyć `DataContractSerializerOperationBehavior` dostosować serializacji klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="f7889-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="f7889-212">Poniższy przykład przedstawia sposób zwiększenia `MaxItemsInObjectGraph` przydziału na kliencie.</span><span class="sxs-lookup"><span data-stu-id="f7889-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
 <span data-ttu-id="f7889-213">Poniżej znajduje się kod równoważne usługi, w przypadku hostowania samoobsługowego.</span><span class="sxs-lookup"><span data-stu-id="f7889-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
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
  
 <span data-ttu-id="f7889-214">W przypadku hostowanych w sieci Web, należy utworzyć nowy `ServiceHost` klasy i dołączyć go przy użyciu fabryki hostów usług.</span><span class="sxs-lookup"><span data-stu-id="f7889-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="f7889-215">Kontrolowanie serializacji ustawień konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f7889-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="f7889-216">`MaxItemsInObjectGraph` i `IgnoreExtensionDataObject` można sterować za pomocą konfiguracji przy użyciu `dataContractSerializer` zachowanie punktu końcowego lub usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f7889-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="f7889-217">Wspólnego typu serializacji, zachowywania wykres obiektu i serializatorów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f7889-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="f7889-218"><xref:System.Runtime.Serialization.DataContractSerializer> Serializuje przy użyciu nazwy kontraktu danych, a nie nazwy typów .NET.</span><span class="sxs-lookup"><span data-stu-id="f7889-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="f7889-219">To jest zgodna z zorientowane na usługę architektura rozwiązań i umożliwia precyzyjną elastyczność — typów .NET, można zmienić bez wpływu na kontraktu danych przesyłanych w sieci.</span><span class="sxs-lookup"><span data-stu-id="f7889-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="f7889-220">W rzadkich przypadkach można serializować rzeczywistej nazwy typów .NET, co wprowadzenie ścisłej sprzężenia między klientem i serwerem, podobnie jak technologię zdalnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7889-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="f7889-221">To nie jest zalecanym rozwiązaniem, z wyjątkiem w rzadkich przypadkach, w których zwykle występują podczas migracji do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z usługi zdalne środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7889-221">This is not a recommended practice, except in rare cases that usually occur when migrating to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] from .NET Framework remoting.</span></span> <span data-ttu-id="f7889-222">W takim przypadku należy użyć <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7889-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="f7889-223"><xref:System.Runtime.Serialization.DataContractSerializer> Zwykle serializuje wykresów obiektów jako drzewa obiektów.</span><span class="sxs-lookup"><span data-stu-id="f7889-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="f7889-224">Oznacza to jeżeli ten sam obiekt jest określona więcej niż raz, jego jest serializowane więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="f7889-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="f7889-225">Rozważmy na przykład `PurchaseOrder` wystąpienia, która ma dwa pola typu o nazwie adresu `billTo` i `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="f7889-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="f7889-226">Jeśli oba pola są ustawione w tym samym wystąpieniu adres, istnieją dwa identyczne wystąpienia adres po serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="f7889-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="f7889-227">Odbywa się, ponieważ nie istnieje standardowy sposób interoperacyjne do reprezentowania wykresów obiektów w pliku XML (z wyjątkiem dostępne w starszej wersji standard SOAP zakodowane <xref:System.Xml.Serialization.XmlSerializer>, zgodnie z opisem w poprzedniej sekcji na `Style` i `Use`).</span><span class="sxs-lookup"><span data-stu-id="f7889-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="f7889-228">Serializacja wykresów obiektów jako drzewa ma niektóre wady, na przykład nie można zserializować wykresów z odwołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="f7889-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="f7889-229">Czasami jest niezbędne przełączyć się do serializacji wykres obiektu wartość true, mimo że nie jest współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="f7889-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="f7889-230">Można to zrobić za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> skonstruowany przy `preserveObjectReferences` ustawiono parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="f7889-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="f7889-231">Czasami wbudowanych serializatorów nie są wystarczająco dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f7889-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="f7889-232">W większości przypadków można nadal używać <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakcji, z których obie <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> pochodzi.</span><span class="sxs-lookup"><span data-stu-id="f7889-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="f7889-233">Poprzednie trzech przypadkach (zachowania typu .NET, zachowywania wykres obiektu i całkowicie niestandardowych `XmlObjectSerializer`— na podstawie serializacji) wymaga niestandardowy serializator są podłączone.</span><span class="sxs-lookup"><span data-stu-id="f7889-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="f7889-234">W tym celu wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f7889-234">To do this, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="f7889-235">Pisanie własnych zachowanie wynikające z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f7889-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2.  <span data-ttu-id="f7889-236">Zastąpienie dwa `CreateSerializer` metod do zwrócenia własny serializator (albo <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> z `preserveObjectReferences` ustawioną `true`, lub własne niestandardowe <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="f7889-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3.  <span data-ttu-id="f7889-237">Przed otwarciem hosta usługi lub tworzenie kanału klienta, Usuń istniejące <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zachowanie i wtyczki w klasie pochodnej niestandardowe utworzone w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="f7889-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f7889-238">Serializacja pojęcia zaawansowane, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="f7889-238"> advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7889-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7889-239">See Also</span></span>  
 [<span data-ttu-id="f7889-240">Używanie klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f7889-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [<span data-ttu-id="f7889-241">Instrukcje: włączanie przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="f7889-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [<span data-ttu-id="f7889-242">Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="f7889-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
