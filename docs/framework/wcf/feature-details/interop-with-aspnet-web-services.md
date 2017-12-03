---
title: "Współdziałanie z usługami ASP.NET w sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd30b2d62d3ecf21027c0225490da6f31113cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="b4039-102">Współdziałanie z usługami ASP.NET w sieci Web</span><span class="sxs-lookup"><span data-stu-id="b4039-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="b4039-103">Współdziałanie między [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web i [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi sieci Web można osiągnąć przez zapewnienie, że usługi implementowane za pomocą obu tych technologii odpowiadają WS-I Basic Profile 1.1 specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="b4039-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="b4039-104">Usługi sieci Web umożliwiających zgodne ze standardem WS-I Basic Profile 1.1 są zgodne z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania dostarczane przez system, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b4039-104"> Web services that conform to WS-I Basic Profile 1.1 are interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="b4039-105">Użyj [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] możliwość dodania <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> atrybuty do interfejsu, a nie na klasę i zapisywania klasy do zaimplementowania interfejsu, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="b4039-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b4039-106">Ta opcja jest preferowana, ponieważ interfejs <xref:System.Web.Services.WebService> atrybutu stanowi kontraktu dla operacji wykonywanych przez usługę mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="b4039-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="b4039-107">Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atrybutu powoduje, że komunikaty kierowane do metody oparte na w pełni kwalifikowaną nazwę elementu treści komunikatu protokołu SOAP, a nie od `SOAPAction` nagłówka HTTP.</span><span class="sxs-lookup"><span data-stu-id="b4039-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b4039-108">używa `SOAPAction` nagłówek HTTP dla routingu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b4039-108"> uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="b4039-109">Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b4039-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="b4039-110">Podczas określania typu danych do użycia z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]usługi sieci Web w oczekiwaniu przyjęcia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b4039-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], do the following:</span></span>  
  
-   <span data-ttu-id="b4039-111">Zdefiniuj typ, za pomocą klasy .NET Framework, a nie schematu XML.</span><span class="sxs-lookup"><span data-stu-id="b4039-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="b4039-112">Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawnie zdefiniuj przestrzeń nazw dla typu.</span><span class="sxs-lookup"><span data-stu-id="b4039-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="b4039-113">Nie należy dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób klasy .NET Framework jest można przetłumaczyć XML.</span><span class="sxs-lookup"><span data-stu-id="b4039-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="b4039-114">Przyjmując takie podejście, powinno być możliwe dokonanie później klasy platformy .NET w kontraktach danych z uwzględnieniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klas są serializowane do przesłania.</span><span class="sxs-lookup"><span data-stu-id="b4039-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="b4039-115">Typy używane w komunikatach przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usługi sieci Web mogą być przetwarzane jako kontraktów danych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji reaguje, między innymi korzyści, lepszej wydajności w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4039-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, among other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
 <span data-ttu-id="b4039-116">Unikaj używania opcji uwierzytelniania dostępnych przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="b4039-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b4039-117">Klienci nie obsługują je.</span><span class="sxs-lookup"><span data-stu-id="b4039-117"> clients do not support them.</span></span> <span data-ttu-id="b4039-118">Jeśli usługa musi być zabezpieczony, użyj opcji dostarczanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ponieważ te opcje są niezawodne i są oparte na standardowych protokołów.</span><span class="sxs-lookup"><span data-stu-id="b4039-118">If a service must be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="b4039-119">Wpływ na wydajność spowodowane ładowania ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="b4039-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="b4039-120">W .NET Framework 3.0, usługi WCF `HttpModule` został zainstalowany w folderze głównym pliku Web.config tak, aby każda aplikacja ASP.NET została włączona WCF.</span><span class="sxs-lookup"><span data-stu-id="b4039-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="b4039-121">To może mieć wpływ na wydajność, aby usunąć `ServiceModel` w pliku Web.config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b4039-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4039-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4039-122">See Also</span></span>  
 [<span data-ttu-id="b4039-123">Porady: Konfigurowanie usługi WCF na potrzeby współdziałania z klientami usługi sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b4039-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
