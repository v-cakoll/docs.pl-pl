---
title: Współdziałanie z usługami ASP.NET w sieci Web
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 3d4416a67d467f60fa381abc648c3a7ea0b9ada1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713330"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="f3687-102">Współdziałanie z usługami ASP.NET w sieci Web</span><span class="sxs-lookup"><span data-stu-id="f3687-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="f3687-103">Współdziałanie między [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web i usług sieci Web Windows Communication Foundation (WCF), można osiągnąć przez zapewnienie, że usługi implementowane przy użyciu obie technologie są zgodne z WS-I Basic Profile 1.1 specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f3687-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="f3687-104">Sieci Web usługi, które odpowiadają WS-I Basic Profile 1.1 są zgodne z klientów programu WCF za pomocą powiązania dostarczane przez system WCF <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f3687-104">Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="f3687-105">Użyj [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] możliwość dodania <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> atrybuty do interfejsu, a nie klasę w celu zapisywania klasy do zaimplementowania interfejsu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f3687-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="f3687-106">Użycie tej opcji jest preferowana, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybut definiuje kontrakt dla operacji wykonywanych przez usługę, która może być ponownie używane z różnymi klasami, które mogą implementować tej samej umowy na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="f3687-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="f3687-107">Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu powoduje, że wiadomości kierowane do metody oparte na w pełni kwalifikowana nazwa elementu treści komunikatu protokołu SOAP, a nie od `SOAPAction` nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3687-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="f3687-108">Korzysta z usługi WCF `SOAPAction` nagłówka HTTP służącą do rozesłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f3687-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="f3687-109">Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje semantycznie taka sama jak XML, do którego jest typem domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typem parametru przestrzeni nazw XML jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f3687-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="f3687-110">Podczas definiowania typu danych do użycia z usługą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]usług, oczekując na przyjęcie WCF sieci Web, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f3687-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting WCF, do the following:</span></span>  
  
-   <span data-ttu-id="f3687-111">Definiowanie typu przy użyciu klas .NET Framework, a nie schematu XML.</span><span class="sxs-lookup"><span data-stu-id="f3687-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="f3687-112">Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawne definiowanie przestrzeni nazw dla typu.</span><span class="sxs-lookup"><span data-stu-id="f3687-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="f3687-113">Nie należy dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeń nazw w celu kontrolowania, jak klasy .NET Framework ma być przetłumaczone na XML.</span><span class="sxs-lookup"><span data-stu-id="f3687-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="f3687-114">Przyjmując takie podejście, powinno być możliwe zapewnienie później klas .NET w kontraktach danych dodając <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klasy są serializowane w celu przesłania go.</span><span class="sxs-lookup"><span data-stu-id="f3687-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="f3687-115">Typy używane w wiadomości według [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web mogą być przetwarzane tak kontraktów danych przez aplikacje WCF, reaguje pozwala między innymi, lepszej wydajności w aplikacjach usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f3687-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="f3687-116">Należy unikać używania opcji uwierzytelniania udostępniane przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="f3687-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="f3687-117">Klienci WCF nie obsługują je.</span><span class="sxs-lookup"><span data-stu-id="f3687-117">WCF clients do not support them.</span></span> <span data-ttu-id="f3687-118">Jeśli usługa musi zostać zabezpieczony, użyj opcji dostępnych przez architekturę WCF, ponieważ te opcje są niezawodne i bazują na standardowych protokołów.</span><span class="sxs-lookup"><span data-stu-id="f3687-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="f3687-119">Wpływ na wydajność spowodowane przez ładowanie HttpModule modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3687-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="f3687-120">W .NET Framework 3.0, WCF `HttpModule` został zainstalowany w folderze głównym pliku Web.config, tak, aby każda aplikacja ASP.NET została włączona WCF.</span><span class="sxs-lookup"><span data-stu-id="f3687-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="f3687-121">To może mieć wpływ na wydajność, dzięki czemu możesz usunąć `ServiceModel` w pliku Web.config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f3687-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3687-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3687-122">See also</span></span>
- [<span data-ttu-id="f3687-123">Instrukcje: Konfigurowanie usługi WCF do współdziałania z klientami usługi sieci Web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f3687-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
