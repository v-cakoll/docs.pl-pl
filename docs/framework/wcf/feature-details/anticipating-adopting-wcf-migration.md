---
title: "Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ecac6917d47604aa66e9cdc0d845e76ad2de5d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="ccf26-102">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie przyszłych migracji.</span><span class="sxs-lookup"><span data-stu-id="ccf26-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="ccf26-103">Aby zapewnić ułatwia migrację przyszłych nowej aplikacji ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], postępuj zgodnie z poprzednim zalecenia, jak również poniższe zalecenia.</span><span class="sxs-lookup"><span data-stu-id="ccf26-103">To ensure an easier future migration of new ASP.NET applications to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="ccf26-104">protokoły</span><span class="sxs-lookup"><span data-stu-id="ccf26-104">Protocols</span></span>  
 <span data-ttu-id="ccf26-105">Wyłącz obsługę programu ASP.NET 2.0 SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="ccf26-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 <span data-ttu-id="ccf26-106">To jest wskazane ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga wiadomości go przy użyciu różnych punktów końcowych zgodnych z różnych protokołów, takich jak SOAP 1.1 i SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="ccf26-106">Doing so is advisable because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="ccf26-107">Usługi sieci Web programu ASP.NET 2.0 jest skonfigurowany do obsługi protokołu SOAP 1.1 i SOAP 1.2, co jest konfiguracją domyślną, a następnie go nie można migrować do przodu do pojedynczego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego pod adresem oryginalnej, które będą na pewno jest zgodny ze wszystkimi ASP Usługa sieci web .NET istniejących klientów.</span><span class="sxs-lookup"><span data-stu-id="ccf26-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="ccf26-108">Również Wybieranie protokołu SOAP 1.2 zamiast 1.1 więcej znacznie ograniczyć klientelę usługi.</span><span class="sxs-lookup"><span data-stu-id="ccf26-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="ccf26-109">Projektowanie usługi</span><span class="sxs-lookup"><span data-stu-id="ccf26-109">Service Development</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ccf26-110">Służy do definiowania kontraktów usług, stosując <xref:System.ServiceModel.ServiceContractAttribute> albo interfejsy lub klasy.</span><span class="sxs-lookup"><span data-stu-id="ccf26-110"> allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="ccf26-111">Zaleca się zastosowanie atrybutu interfejs, a nie do klasy, ponieważ spowoduje to tworzy definicję kontraktu, który może być różnorodnie zaimplementowany przez dowolną liczbę klas.</span><span class="sxs-lookup"><span data-stu-id="ccf26-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="ccf26-112">Program ASP.NET 2.0 obsługuje opcję stosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klasy.</span><span class="sxs-lookup"><span data-stu-id="ccf26-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="ccf26-113">Jak już wspomniano, istnieje jednak usterką w programie ASP.NET 2.0, w którym parametr Namespace <xref:System.Web.Services.WebService> atrybut nie ma znaczenia, gdy ten atrybut jest stosowany do interfejsu zamiast klasy.</span><span class="sxs-lookup"><span data-stu-id="ccf26-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="ccf26-114">Ponieważ ogólnie jest zalecane, aby zmodyfikować przestrzeni nazw usługi z wartością domyślną http://tempuri.org przy użyciu parametru Namespace <xref:System.Web.Services.WebService> atrybutu, co powinno być kontynuowane Definiowanie usług sieci Web ASP.NET, stosując <xref:System.ServiceModel.ServiceContractAttribute> Atrybut interfejsy lub klasy.</span><span class="sxs-lookup"><span data-stu-id="ccf26-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="ccf26-115">Ma małego kodu, jak to możliwe w metodach, według których te interfejsy są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="ccf26-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="ccf26-116">Niech delegowania ich pracy na inne grupy.</span><span class="sxs-lookup"><span data-stu-id="ccf26-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="ccf26-117">Nowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typów usług można następnie delegować merytorycznych działanie tych klas.</span><span class="sxs-lookup"><span data-stu-id="ccf26-117">New [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="ccf26-118">Jawne nazwy operacji usługi za pomocą `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ccf26-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="ccf26-119">Jest ważne, ponieważ domyślne nazwy operacji w programie ASP.NET są inne niż domyślne nazwy dostarczonych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccf26-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="ccf26-120">Zapewniając jawne nazwy, można uniknąć polegania na domyślne.</span><span class="sxs-lookup"><span data-stu-id="ccf26-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="ccf26-121">Nie implementuje operacji usługi sieci Web ASP.NET za pomocą metod polimorficznym, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie obsługuje operacji implementującej za pomocą metod polimorficznym.</span><span class="sxs-lookup"><span data-stu-id="ccf26-121">Do not implement ASP.NET Web service operations with polymorphic methods, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="ccf26-122">Użyj <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> o podanie wartości jawne nagłówki SOAPAction HTTP przez HTTP żądania będą kierowane do metod.</span><span class="sxs-lookup"><span data-stu-id="ccf26-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="ccf26-123">Biorąc to rozwiązanie zostanie obejścia konieczności polegać na domyślne wartości SOAPAction używanych przez platformę ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są takie same.</span><span class="sxs-lookup"><span data-stu-id="ccf26-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] being the same.</span></span>  
  
-   <span data-ttu-id="ccf26-124">Unikaj stosowania rozszerzeń protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ccf26-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="ccf26-125">Jeśli wymagane są rozszerzenia protokołu SOAP, następnie określić, czy cel, dla których są one są uznawane za jest funkcją, która jest już obsługiwane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccf26-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="ccf26-126">Jeśli w rzeczywistości jest wielkość liter, rozważenia opcja nie przyjmuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] od razu.</span><span class="sxs-lookup"><span data-stu-id="ccf26-126">If that is indeed the case, then reconsider the choice to not adopt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="ccf26-127">Stan zarządzania</span><span class="sxs-lookup"><span data-stu-id="ccf26-127">State Management</span></span>  
 <span data-ttu-id="ccf26-128">Unikaj używania do zarządzania stanem w usługach.</span><span class="sxs-lookup"><span data-stu-id="ccf26-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="ccf26-129">Nie tylko zachowanie stanu mogą naruszyć skalowalność aplikacji, ale mechanizmy zarządzania stan aplikacji ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bardzo różnią się, mimo że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje mechanizmów ASP.NET w zgodności z platformą ASP.NET tryb.</span><span class="sxs-lookup"><span data-stu-id="ccf26-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are very different, although [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="ccf26-130">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="ccf26-130">Exception Handling</span></span>  
 <span data-ttu-id="ccf26-131">Projektowanie struktury typów danych, aby być wysyłane i odbierane przez usługę, również struktury projektu do reprezentowania różnych typów wyjątków, które mogą wystąpić w ramach usługi co może chcieć przekazania do klienta.</span><span class="sxs-lookup"><span data-stu-id="ccf26-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="ccf26-132">Zapewnianie takich klas możliwości serializacji się do pliku XML:</span><span class="sxs-lookup"><span data-stu-id="ccf26-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="ccf26-133">Klasy, następnie może służyć do Podaj szczegóły, aby jawnie zgłoszony <xref:System.Web.Services.Protocols.SoapException> wystąpień:</span><span class="sxs-lookup"><span data-stu-id="ccf26-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="ccf26-134">Te klasy wyjątków będzie łatwo wielokrotnego użytku z[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.FaultException%601> klasę, aby zgłosić nową`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="ccf26-134">These exception classes will be readily reusable with the[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="ccf26-135">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ccf26-135">Security</span></span>  
 <span data-ttu-id="ccf26-136">Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ccf26-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="ccf26-137">Unikaj jako ich użycie za pomocą profilów programu ASP.NET 2.0 ograniczałyby trybu integracji ASP.NET Jeśli usługa został zmigrowany do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccf26-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
-   <span data-ttu-id="ccf26-138">Unikaj używania listy kontroli dostępu do kontrolowania dostępu do usług, jako usługi sieci Web ASP.NET obsługuje listy ACL za pomocą Internet Information Services (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie — ponieważ usług sieci Web ASP.NET są zależne od usług IIS do hostowania i WCF niekoniecznie musi być obsługiwana przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="ccf26-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="ccf26-139">Należy rozważyć użycie dostawców ról ASP.NET 2.0 w celu autoryzowania dostępu do zasobów usługi.</span><span class="sxs-lookup"><span data-stu-id="ccf26-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf26-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccf26-140">See Also</span></span>  
 [<span data-ttu-id="ccf26-141">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="ccf26-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
