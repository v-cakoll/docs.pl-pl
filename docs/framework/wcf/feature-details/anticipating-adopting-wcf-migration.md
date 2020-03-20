---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185473"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="ad754-102">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="ad754-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="ad754-103">Aby zapewnić łatwiejszą migrację nowych aplikacji ASP.NET do WCF, postępuj zgodnie z poprzednimi zaleceniami, a także następującymi zaleceniami.</span><span class="sxs-lookup"><span data-stu-id="ad754-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="ad754-104">Protokoły</span><span class="sxs-lookup"><span data-stu-id="ad754-104">Protocols</span></span>  
 <span data-ttu-id="ad754-105">Wyłącz obsługę protokołu ASP.NET 2.0 dla protokołu SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="ad754-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="ad754-106">Jest to wskazane, ponieważ WCF wymaga komunikatów zgodnych z różnymi protokołami, takich jak SOAP 1.1 i SOAP 1.2, aby przejść przy użyciu różnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ad754-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="ad754-107">Jeśli usługa sieci Web ASP.NET 2.0 jest skonfigurowana do obsługi zarówno protokołu SOAP 1.1, jak i PROTOKOŁU SOAP 1.2, który jest konfiguracją domyślną, nie można jej przeprowadzić migracji do jednego punktu końcowego WCF pod oryginalnym adresem, który z pewnością byłby zgodny ze wszystkimi ASP.NET Web istniejących klientów serwisu.</span><span class="sxs-lookup"><span data-stu-id="ad754-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="ad754-108">Również wybranie protokołu SOAP 1.2 zamiast 1.1 spowoduje bardziej poważne ograniczenie klienteli usługi.</span><span class="sxs-lookup"><span data-stu-id="ad754-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="ad754-109">Rozwój usług</span><span class="sxs-lookup"><span data-stu-id="ad754-109">Service Development</span></span>  
 <span data-ttu-id="ad754-110">WCF umożliwia definiowanie umów serwisowych <xref:System.ServiceModel.ServiceContractAttribute> przez zastosowanie albo do interfejsów lub klas.</span><span class="sxs-lookup"><span data-stu-id="ad754-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="ad754-111">Zaleca się zastosowanie atrybutu do interfejsu, a nie do klasy, ponieważ w ten sposób tworzy definicję kontraktu, który może być różnie implementowane przez dowolną liczbę klas.</span><span class="sxs-lookup"><span data-stu-id="ad754-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="ad754-112">ASP.NET 2.0 obsługuje opcję stosowania atrybutu <xref:System.Web.Services.WebService> do interfejsów, a także klas.</span><span class="sxs-lookup"><span data-stu-id="ad754-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="ad754-113">Jednak, jak już wspomniano, istnieje wada w ASP.NET 2.0, za pomocą <xref:System.Web.Services.WebService> którego Namespace parametr atrybutu nie ma wpływu, gdy ten atrybut jest stosowany do interfejsu, a nie klasy.</span><span class="sxs-lookup"><span data-stu-id="ad754-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="ad754-114">Ponieważ ogólnie zaleca się modyfikowanie obszaru nazw usługi z wartości `http://tempuri.org`domyślnej, używając parametru Obszar nazw <xref:System.Web.Services.WebService> atrybutu, należy kontynuować definiowanie <xref:System.ServiceModel.ServiceContractAttribute> ASP.NET usług sieci Web, stosując atrybut do interfejsów lub klas.</span><span class="sxs-lookup"><span data-stu-id="ad754-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="ad754-115">Mają jak najmniejszy kod, jak to możliwe w metodach, za pomocą których te interfejsy są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="ad754-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="ad754-116">Niech delegują swoją pracę do innych klas.</span><span class="sxs-lookup"><span data-stu-id="ad754-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="ad754-117">Nowe typy usług WCF może następnie również delegować ich pracy merytorycznej do tych klas.</span><span class="sxs-lookup"><span data-stu-id="ad754-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="ad754-118">Podaj jawne nazwy operacji `MessageName` usługi przy <xref:System.Web.Services.WebMethodAttribute>użyciu parametru .</span><span class="sxs-lookup"><span data-stu-id="ad754-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="ad754-119">Jest to ważne, ponieważ domyślne nazwy operacji w ASP.NET różnią się od nazw domyślnych dostarczonych przez WCF.</span><span class="sxs-lookup"><span data-stu-id="ad754-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="ad754-120">Podając jawne nazwy, można uniknąć polegania na domyślnych.</span><span class="sxs-lookup"><span data-stu-id="ad754-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="ad754-121">Nie należy implementować ASP.NET operacji usługi sieci Web metod polimorficznych, ponieważ WCF nie obsługuje implementowania operacji z metodami polimorficznymi.</span><span class="sxs-lookup"><span data-stu-id="ad754-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="ad754-122">Użyj, <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> aby podać jawne wartości dla nagłówków HTTP SOAPAction, za pomocą których żądania HTTP będą kierowane do metod.</span><span class="sxs-lookup"><span data-stu-id="ad754-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="ad754-123">Przyjęcie tego podejścia będzie obejść konieczności polegać na domyślne soapaction wartości używane przez ASP.NET i WCF są takie same.</span><span class="sxs-lookup"><span data-stu-id="ad754-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="ad754-124">Unikaj używania rozszerzeń SOAP.</span><span class="sxs-lookup"><span data-stu-id="ad754-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="ad754-125">Jeśli rozszerzenia protokołu SOAP są wymagane, a następnie określić, czy celem, dla którego są one rozważane jest funkcja, która jest już dostarczona przez WCF.</span><span class="sxs-lookup"><span data-stu-id="ad754-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="ad754-126">Jeśli rzeczywiście tak jest, to ponownie rozważyć wybór nie przyjąć WCF od razu.</span><span class="sxs-lookup"><span data-stu-id="ad754-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="ad754-127">Zarządzanie państwem</span><span class="sxs-lookup"><span data-stu-id="ad754-127">State Management</span></span>  
 <span data-ttu-id="ad754-128">Unikaj konieczności utrzymywania stanu w usługach.</span><span class="sxs-lookup"><span data-stu-id="ad754-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="ad754-129">Nie tylko utrzymanie stanu mają tendencję do naruszenia skalowalności aplikacji, ale mechanizmy zarządzania stanem ASP.NET i WCF są bardzo różne, chociaż WCF obsługuje mechanizmy ASP.NET w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ad754-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="ad754-130">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="ad754-130">Exception Handling</span></span>  
 <span data-ttu-id="ad754-131">Podczas projektowania struktur typów danych, które mają być wysyłane i odbierane przez usługę, należy również projektować struktury reprezentujące różne typy wyjątków, które mogą wystąpić w ramach usługi, które można przekazać klientowi.</span><span class="sxs-lookup"><span data-stu-id="ad754-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ad754-132">Daj takim klasom możliwość serializacji się do XML:</span><span class="sxs-lookup"><span data-stu-id="ad754-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="ad754-133">Klasy mogą następnie służyć do zapewnienia szczegółów <xref:System.Web.Services.Protocols.SoapException> dla jawnie zgłoszonych wystąpień:</span><span class="sxs-lookup"><span data-stu-id="ad754-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="ad754-134">Te klasy wyjątków będą łatwo wielokrotnego pożytego z klasą WCF, <xref:System.ServiceModel.FaultException%601> aby`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="ad754-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="ad754-135">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ad754-135">Security</span></span>  
 <span data-ttu-id="ad754-136">Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ad754-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="ad754-137">Należy unikać używania ASP.NET 2.0 Profile, ponieważ ich używanie ograniczyłoby użycie trybu integracji ASP.NET, jeśli usługa została zmigrowana do WCF.</span><span class="sxs-lookup"><span data-stu-id="ad754-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="ad754-138">Unikaj używania list ACL do kontrolowania dostępu do usług, ponieważ ASP.NET usług sieci Web obsługuje listy ACL korzystające z internetowych usług informacyjnych (IIS), WCF nie — ponieważ ASP.NET usług sieci Web zależą od usług IIS dla hostingu, a WCF nie musi być hostowany w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="ad754-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="ad754-139">Należy rozważyć użycie ASP.NET 2.0 dostawców ról do autoryzowania dostępu do zasobów usługi.</span><span class="sxs-lookup"><span data-stu-id="ad754-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad754-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad754-140">See also</span></span>

- [<span data-ttu-id="ad754-141">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="ad754-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
