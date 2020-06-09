---
title: Współdziałanie z usługami ASP.NET w sieci Web
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f38209ffe2161e58528a108b29e730665a65da37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598869"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="59e5b-102">Współdziałanie z usługami ASP.NET w sieci Web</span><span class="sxs-lookup"><span data-stu-id="59e5b-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="59e5b-103">Współdziałanie między usługami sieci Web ASP.NET Web Services i Windows Communication Foundation (WCF) można uzyskać, upewniając się, że usługi zaimplementowane przy użyciu obu technologii są zgodne ze specyfikacją WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="59e5b-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="59e5b-104">Usługi sieci Web ASP.NET, które są zgodne ze standardem WS-I Basic Profile 1,1, współdziałają z klientami programu WCF przy użyciu powiązania dostarczonego przez system <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="59e5b-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="59e5b-105">Użyj opcji ASP.NET 2,0, aby dodać <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> atrybuty i do interfejsu, a nie do klasy, i napisać klasę, aby zaimplementować interfejs, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="59e5b-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="59e5b-106">Użycie tej opcji jest preferowane, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybutem stanowi kontrakt dla operacji wykonywanych przez usługę, które mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="59e5b-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="59e5b-107">Należy unikać używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu, aby komunikaty były kierowane do metod opartych na w pełni kwalifikowanej nazwie elementu treści komunikatu protokołu SOAP, a nie w `SOAPAction` nagłówku HTTP.</span><span class="sxs-lookup"><span data-stu-id="59e5b-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="59e5b-108">Funkcja WCF używa `SOAPAction` nagłówka HTTP do routingu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="59e5b-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="59e5b-109">KOD XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializowany jest typ domyślnie jest semantycznie identyczny z XML, do którego jest <xref:System.Runtime.Serialization.DataContractSerializer> serializowany typ, pod warunkiem, że przestrzeń nazw dla kodu XML jest jawnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="59e5b-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="59e5b-110">Podczas definiowania typu danych do użycia z usługami ASP. NETWeb w celu przewidzenia wdrożenia WCF należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="59e5b-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="59e5b-111">Zdefiniuj typ przy użyciu klas .NET Framework, a nie schematu XML.</span><span class="sxs-lookup"><span data-stu-id="59e5b-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="59e5b-112">Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, używając tej ostatniej, aby jawnie zdefiniować przestrzeń nazw dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="59e5b-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="59e5b-113">Nie dodawaj dodatkowych atrybutów z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób tłumaczenia klasy .NET Framework na XML.</span><span class="sxs-lookup"><span data-stu-id="59e5b-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="59e5b-114">Przyjmując takie podejście, powinno być możliwe późniejsze przekazanie klas .NET do kontraktów danych z dodaniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez znacząco zmiany kodu XML, do którego klasy są serializowane do transmisji.</span><span class="sxs-lookup"><span data-stu-id="59e5b-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="59e5b-115">Typy używane w komunikatach przez usługi sieci Web ASP.NET mogą być przetwarzane jako Kontrakty danych przez aplikacje WCF, a wśród innych korzyści, lepsza wydajność w aplikacjach WCF.</span><span class="sxs-lookup"><span data-stu-id="59e5b-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="59e5b-116">Należy unikać używania opcji uwierzytelniania zapewnianych przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="59e5b-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="59e5b-117">Klienci WCF nie obsługują tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="59e5b-117">WCF clients do not support them.</span></span> <span data-ttu-id="59e5b-118">Jeśli usługa musi być zabezpieczona, użyj opcji dostarczonych przez program WCF, ponieważ te opcje są niezawodne i są oparte na protokołach standardowych.</span><span class="sxs-lookup"><span data-stu-id="59e5b-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="59e5b-119">Wpływ na wydajność spowodowany ładowaniem modułu ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="59e5b-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="59e5b-120">W .NET Framework 3,0 `HttpModule` Funkcja WCF została zainstalowana w głównym pliku Web. config w taki sposób, że każda aplikacja ASP.NET była włączona w ramach funkcji WCF.</span><span class="sxs-lookup"><span data-stu-id="59e5b-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="59e5b-121">Może to mieć wpływ na wydajność, dlatego można usunąć `ServiceModel` plik Web. config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="59e5b-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="59e5b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59e5b-122">See also</span></span>

- [<span data-ttu-id="59e5b-123">Instrukcje: konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi ASP.NET w sieci Web</span><span class="sxs-lookup"><span data-stu-id="59e5b-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](config-wcf-service-with-aspnet-web-service.md)
