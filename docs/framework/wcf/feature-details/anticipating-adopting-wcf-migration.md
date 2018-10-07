---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 171a31b375eae4c032849c2a1c2090f5d9ff856f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837404"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="1aba6-102">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="1aba6-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="1aba6-103">Aby zapewnić łatwiejsze migracji w przyszłości nowej aplikacji ASP.NET do programu WCF, postępuj zgodnie z poprzednim zalecenia, a także poniższe zalecenia.</span><span class="sxs-lookup"><span data-stu-id="1aba6-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="1aba6-104">Protokoły</span><span class="sxs-lookup"><span data-stu-id="1aba6-104">Protocols</span></span>  
 <span data-ttu-id="1aba6-105">Wyłączanie obsługi programu ASP.NET 2.0 protokołu SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="1aba6-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="1aba6-106">Ten sposób jest zalecane, ponieważ WCF wymaga wiadomości go przy użyciu różnych punktów końcowych zgodnych z różnych protokołów, takich jak SOAP 1.1 i SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="1aba6-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="1aba6-107">Jeśli sieci Web ASP.NET 2.0 usługa jest skonfigurowana do obsługi protokołu SOAP 1.1 i SOAP 1.2, która jest domyślna konfiguracja, a następnie nie może być migrowane do przodu do jednym punkcie końcowym WCF pod adresem oryginalnej, która byłaby bez obaw być zgodne ze wszystkimi sieci Web platformy ASP.NET istniejący klienci usługi.</span><span class="sxs-lookup"><span data-stu-id="1aba6-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="1aba6-108">Również wybranie SOAP 1.2 zamiast 1.1 bardziej poważnie ograniczy klientelę usługi.</span><span class="sxs-lookup"><span data-stu-id="1aba6-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="1aba6-109">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="1aba6-109">Service Development</span></span>  
 <span data-ttu-id="1aba6-110">Usługi WCF służy do definiowania kontraktów usług, stosując <xref:System.ServiceModel.ServiceContractAttribute> interfejsy lub klasy.</span><span class="sxs-lookup"><span data-stu-id="1aba6-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="1aba6-111">Zalecane jest aby zastosować atrybut do interfejsu, a nie do klasy, ponieważ spowoduje to więc tworzy definicję kontraktu, który może być różnorodnie implementowany przez dowolną liczbę klas.</span><span class="sxs-lookup"><span data-stu-id="1aba6-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="1aba6-112">Program ASP.NET 2.0 obsługuje opcję stosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klasy.</span><span class="sxs-lookup"><span data-stu-id="1aba6-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="1aba6-113">Jak już wspomniano, istnieje jednak wadę w programie ASP.NET 2.0 za pomocą którego parametr Namespace <xref:System.Web.Services.WebService> atrybut nie ma wpływu Jeśli ten atrybut jest stosowany do interfejsu, a nie klasę.</span><span class="sxs-lookup"><span data-stu-id="1aba6-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="1aba6-114">Ponieważ jest na ogół do modyfikowania przestrzeni nazw usługi z wartością domyślną `http://tempuri.org`, za pomocą parametru Namespace <xref:System.Web.Services.WebService> atrybutu, jeden powinno być kontynuowane Definiowanie usług sieci Web ASP.NET, stosując <xref:System.ServiceModel.ServiceContractAttribute> Atrybut interfejsy lub klasy.</span><span class="sxs-lookup"><span data-stu-id="1aba6-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="1aba6-115">Jak to możliwe za pomocą metod, które są zdefiniowane te interfejsy, należy mieć jako niewielkiej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="1aba6-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="1aba6-116">Poproś delegować swoją pracę dla innych klas.</span><span class="sxs-lookup"><span data-stu-id="1aba6-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="1aba6-117">Nowe typy usług WCF następnie może również delegować swoją pracę merytorycznych do tych klas.</span><span class="sxs-lookup"><span data-stu-id="1aba6-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="1aba6-118">Podać jawne nazwy dla operacji usługi za pomocą `MessageName` parametru <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1aba6-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="1aba6-119">To jest ważne, ponieważ z domyślnymi nazwami operacje w programie ASP.NET: różnią się od nazwy domyślne, dostarczone przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="1aba6-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="1aba6-120">Dostarczając jawnej nazwy, można uniknąć, opierając się na domyślne.</span><span class="sxs-lookup"><span data-stu-id="1aba6-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="1aba6-121">Nie należy implementować operacji usługi sieci Web platformy ASP.NET za pomocą metod polimorficznych, ponieważ WCF nie obsługuje operacji implementującej za pomocą metod polimorficznych.</span><span class="sxs-lookup"><span data-stu-id="1aba6-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="1aba6-122">Użyj <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> podać jawne wartości nagłówków SOAPAction HTTP, przez które HTTP żądania będą kierowane do metody.</span><span class="sxs-lookup"><span data-stu-id="1aba6-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="1aba6-123">W ten sposób obejścia, konieczności opierają się na domyślnej wartości SOAPAction używane przez program ASP.NET i WCF jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="1aba6-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
-   <span data-ttu-id="1aba6-124">Należy unikać używania rozszerzeń protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="1aba6-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="1aba6-125">Jeśli rozszerzenia SOAP, które są wymagane, określ, czy celem, dla którego one są uznawane za to funkcja, która znajduje się już przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="1aba6-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="1aba6-126">Jeśli tak jest rzeczywiście tak, ponowne rozpatrzenie możliwość nie przyjmują razu WCF.</span><span class="sxs-lookup"><span data-stu-id="1aba6-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="1aba6-127">Zarządzanie stanem</span><span class="sxs-lookup"><span data-stu-id="1aba6-127">State Management</span></span>  
 <span data-ttu-id="1aba6-128">Uniknąć konieczności zarządzania stanem w usługach.</span><span class="sxs-lookup"><span data-stu-id="1aba6-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="1aba6-129">Nie tylko jest zachowanie stanu mają tendencję do naruszenia bezpieczeństwa skalowalność aplikacji, ale mechanizmami zarządzania stan programu ASP.NET i WCF różnią się bardzo, chociaż WCF obsługuje mechanizmów platformy ASP.NET w trybie zgodności w programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1aba6-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="1aba6-130">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="1aba6-130">Exception Handling</span></span>  
 <span data-ttu-id="1aba6-131">Projektowanie struktury typów danych, aby być wysyłane i odbierane przez usługę, również struktury projektu do reprezentowania różne rodzaje wyjątków, które mogą wystąpić w ramach usługi ten. może chcieć przekazania do klienta.</span><span class="sxs-lookup"><span data-stu-id="1aba6-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="1aba6-132">Zapewnianie takich klas możliwości serializacji się do pliku XML:</span><span class="sxs-lookup"><span data-stu-id="1aba6-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="1aba6-133">Klasy mogą następnie służyć do Podaj szczegóły, aby jawnie zgłoszony <xref:System.Web.Services.Protocols.SoapException> wystąpień:</span><span class="sxs-lookup"><span data-stu-id="1aba6-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="1aba6-134">Te klasy wyjątków będzie łatwo wielokrotnego użytku z programem WCF<xref:System.ServiceModel.FaultException%601> klasy, aby wygenerować nowy `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="1aba6-134">These exception classes will be readily reusable with the WCF<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="1aba6-135">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="1aba6-135">Security</span></span>  
 <span data-ttu-id="1aba6-136">Poniżej przedstawiono kilka zaleceń dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1aba6-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="1aba6-137">Należy unikać przy użyciu profilów platformy ASP.NET 2.0 jako ich użycie będzie ograniczyć użycie trybu integracji programu ASP.NET, jeśli usługa została poddana migracji do programu WCF.</span><span class="sxs-lookup"><span data-stu-id="1aba6-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
-   <span data-ttu-id="1aba6-138">Należy unikać używania listy ACL do kontrolowania dostępu do usług, jako usług sieci Web platformy ASP.NET — obsługuje listy kontroli dostępu przy użyciu usług Internet Information Services (IIS), usługi WCF nie — ponieważ usług sieci Web programu ASP.NET, są zależne od usług IIS do hostowania i usługi WCF nie musi być hostowane w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="1aba6-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="1aba6-139">Należy rozważyć użycie dostawcy roli programu ASP.NET 2.0 do autoryzowania dostępu do zasobów usługi.</span><span class="sxs-lookup"><span data-stu-id="1aba6-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aba6-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aba6-140">See Also</span></span>  
 [<span data-ttu-id="1aba6-141">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="1aba6-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
