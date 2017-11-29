---
title: "Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f60b2566895acfd7d2b749729fab9c3f5deb20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="f34f0-102">Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="f34f0-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="f34f0-103">Jeśli obecnie za pomocą programu ASP.NET, a przewiduje się przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w przyszłości, w tym temacie przedstawiono wskazówki dotyczące upewnij się, że nowe usługi sieci Web ASP.NET będzie współpracować razem z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f34f0-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="f34f0-104">Ogólne zalecenia</span><span class="sxs-lookup"><span data-stu-id="f34f0-104">General Recommendations</span></span>  
 <span data-ttu-id="f34f0-105">Przyjmuje ASP.NET 2.0 dla wszystkich nowych usług.</span><span class="sxs-lookup"><span data-stu-id="f34f0-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="f34f0-106">W ten sposób umożliwi dostęp do ulepszenia i ulepszenia nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="f34f0-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="f34f0-107">Jednak również umożliwi umożliwiające korzystanie ze składników programu ASP.NET 2.0 razem z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składniki w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f34f0-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="f34f0-108">protokoły</span><span class="sxs-lookup"><span data-stu-id="f34f0-108">Protocols</span></span>  
 <span data-ttu-id="f34f0-109">Skorzystać z funkcji nowego składnika ASP.NET 2.0 weryfikowania zgodności ze standardem WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="f34f0-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="f34f0-110">Usługi sieci Web ASP.NET, które są zgodne ze standardem WS-I Basic Profile 1.1 będzie współdziałać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wstępnie zdefiniowanych powiązań, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f34f0-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="f34f0-111">Projektowanie usługi</span><span class="sxs-lookup"><span data-stu-id="f34f0-111">Service Development</span></span>  
 <span data-ttu-id="f34f0-112">Unikaj używania <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> w pełni kwalifikowaną nazwę elementu treści komunikatu protokołu SOAP, a nie w nagłówku SOAPAction HTTP na podstawie atrybutu powoduje, że komunikaty kierowane do metody.</span><span class="sxs-lookup"><span data-stu-id="f34f0-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f34f0-113">używa nagłówka SOAPAction HTTP dla routingu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f34f0-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="f34f0-114">Reprezentacja wartości danych</span><span class="sxs-lookup"><span data-stu-id="f34f0-114">Data Representation</span></span>  
 <span data-ttu-id="f34f0-115">Plik XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f34f0-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="f34f0-116">Gdy Definiowanie typu danych do użycia z sieci Web ASP.NET usług w oczekiwaniu przyjęcia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w przyszłości, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f34f0-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="f34f0-117">Zdefiniuj typ, za pomocą klasy .NET Framework, a nie schematu XML.</span><span class="sxs-lookup"><span data-stu-id="f34f0-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="f34f0-118">Dodaj tylko <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do klasy, za pomocą jego jawnie zdefiniuj przestrzeń nazw dla typu.</span><span class="sxs-lookup"><span data-stu-id="f34f0-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="f34f0-119">Czy nie dodawać dodatkowe atrybuty z <xref:System.Xml.Serialization> przestrzeni nazw, aby kontrolować sposób klasy .NET Framework jest można przetłumaczyć XML.</span><span class="sxs-lookup"><span data-stu-id="f34f0-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="f34f0-120">Przyjmując takie podejście, powinno być możliwe dokonanie później klasy platformy .NET w kontraktach danych z uwzględnieniem <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> bez zmiany znacznie XML, do którego klas są serializowane do przesłania.</span><span class="sxs-lookup"><span data-stu-id="f34f0-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="f34f0-121">Typy używane w komunikatach przez usługi sieci Web ASP.NET będzie można przetwarzać jako kontraktów danych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji reaguje, między innymi korzyści, lepszej wydajności w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f34f0-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f34f0-122">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f34f0-122">Security</span></span>  
 <span data-ttu-id="f34f0-123">Unikaj używania opcji uwierzytelniania dostępnych przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="f34f0-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f34f0-124">Klienci nie obsługują je.</span><span class="sxs-lookup"><span data-stu-id="f34f0-124"> clients do not support them.</span></span> <span data-ttu-id="f34f0-125">Jeśli usługa musi być zabezpieczony, użyj opcji dostarczanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ponieważ te opcje są bardziej rozbudowane i są oparte na standardowych protokołów.</span><span class="sxs-lookup"><span data-stu-id="f34f0-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34f0-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f34f0-126">See Also</span></span>  
 [<span data-ttu-id="f34f0-127">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji.</span><span class="sxs-lookup"><span data-stu-id="f34f0-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
