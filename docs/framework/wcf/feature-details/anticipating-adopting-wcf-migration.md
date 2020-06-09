---
title: 'Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: b43f509bd49ebe89d7ed0be4c37b3ed179aaeb8c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576502"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="4d7ae-102">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="4d7ae-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="4d7ae-103">Aby zapewnić łatwiejsze Migrowanie nowych aplikacji ASP.NET do usługi WCF, postępuj zgodnie z powyższymi zaleceniami, a także z poniższymi zaleceniami.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="4d7ae-104">Protokoły</span><span class="sxs-lookup"><span data-stu-id="4d7ae-104">Protocols</span></span>  
 <span data-ttu-id="4d7ae-105">Wyłącz obsługę protokołu SOAP 1,2 w programie ASP.NET 2.0:</span><span class="sxs-lookup"><span data-stu-id="4d7ae-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="4d7ae-106">Jest to zalecane, ponieważ WCF wymaga komunikatów zgodnych z różnymi protokołami, takimi jak SOAP 1,1 i SOAP 1,2, aby przejść przy użyciu różnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="4d7ae-107">Jeśli usługa sieci Web ASP.NET 2,0 jest skonfigurowana do obsługi zarówno protokołu SOAP 1,1, jak i protokołu SOAP 1,2, który jest domyślną konfiguracją, nie można migrować do przodu do pojedynczego punktu końcowego WCF na oryginalnym adresie, który będzie miał być zgodny ze wszystkimi istniejącymi klientami usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="4d7ae-108">Ponadto wybranie protokołu SOAP 1,2 zamiast 1,1 będzie bardziej poważnie ograniczyć Clientele usługi.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="4d7ae-109">Opracowywanie usług</span><span class="sxs-lookup"><span data-stu-id="4d7ae-109">Service Development</span></span>  
 <span data-ttu-id="4d7ae-110">Funkcja WCF umożliwia definiowanie kontraktów usługi przez zastosowanie ich <xref:System.ServiceModel.ServiceContractAttribute> do interfejsów lub do klas.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="4d7ae-111">Zaleca się stosowanie atrybutu do interfejsu, a nie do klasy, ponieważ w ten sposób tworzy definicję kontraktu, który może być wdrożony przez dowolną liczbę klas.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="4d7ae-112">ASP.NET 2,0 obsługuje opcję zastosowania <xref:System.Web.Services.WebService> atrybutu do interfejsów, a także klas.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="4d7ae-113">Jednak jak już wspomniano, istnieje wada w ASP.NET 2,0, przez który parametr Namespace <xref:System.Web.Services.WebService> atrybutu nie ma wpływu, gdy ten atrybut jest stosowany do interfejsu, a nie klasy.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="4d7ae-114">Ponieważ ogólnie zaleca się zmodyfikowanie przestrzeni nazw usługi z wartości domyślnej, `http://tempuri.org` przy użyciu parametru przestrzeni nazw <xref:System.Web.Services.WebService> atrybutu, jeden powinien kontynuować Definiowanie usług sieci Web ASP.NET przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsów lub do klas.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="4d7ae-115">Mieć możliwie najmniejszą ilość kodu w metodach, za pomocą których są zdefiniowane te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="4d7ae-116">Umożliwiają delegowanie pracy do innych klas.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="4d7ae-117">Nowe typy usługi WCF mogą następnie delegować swoją merytoryczną służbę do tych klas.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="4d7ae-118">Podaj jawne nazwy dla operacji usługi przy użyciu `MessageName` parametru <xref:System.Web.Services.WebMethodAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4d7ae-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="4d7ae-119">Jest to ważne, ponieważ domyślne nazwy operacji w programie ASP.NET różnią się od domyślnych nazw dostarczonych przez program WCF.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="4d7ae-120">Dostarczając jawne nazwy, można uniknąć polegania na domyślnych.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="4d7ae-121">Nie należy implementować operacji usługi sieci Web ASP.NET za pomocą metod polimorficznych, ponieważ WCF nie obsługuje implementowania operacji przy użyciu metod polimorficznych.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="4d7ae-122">Użyj, <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> Aby podać jawne wartości w nagłówkach HTTP SoapAction, za pomocą których żądania HTTP będą kierowane do metod.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="4d7ae-123">Zastosowanie tej metody spowoduje obejście tego, że należy zależeć od domyślnych wartości SOAPAction używanych przez ASP.NET i WCF.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="4d7ae-124">Unikaj używania rozszerzeń SOAP.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="4d7ae-125">Jeśli wymagane są rozszerzenia SOAP, określ, czy cel, dla którego są brane pod uwagę, jest funkcją, która jest już świadczona przez WCF.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="4d7ae-126">Jeśli tak naprawdę ma to miejsce, należy ponownie rozważyć wybór, aby nie zastosować funkcji WCF od razu.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="4d7ae-127">Zarządzanie stanem</span><span class="sxs-lookup"><span data-stu-id="4d7ae-127">State Management</span></span>  
 <span data-ttu-id="4d7ae-128">Unikaj konieczności zachowywania stanu usług.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="4d7ae-129">Nie tylko jest utrzymany stan, który ma na celu złamanie skalowalności aplikacji, ale mechanizmy zarządzania Stanami ASP.NET i WCF są bardzo różne, chociaż WCF obsługuje mechanizmy ASP.NET w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="4d7ae-130">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="4d7ae-130">Exception Handling</span></span>  
 <span data-ttu-id="4d7ae-131">Podczas projektowania struktur typów danych, które mają być wysyłane i odbierane przez usługę, należy również projektować struktury reprezentujące różne typy wyjątków, które mogą wystąpić w ramach usługi, która może być przekazana do klienta.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="4d7ae-132">Nadaj tym klasom możliwość serializacji do kodu XML:</span><span class="sxs-lookup"><span data-stu-id="4d7ae-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="4d7ae-133">Klasy mogą następnie służyć do podania szczegółów dla jawnie zgłoszonych <xref:System.Web.Services.Protocols.SoapException> wystąpień:</span><span class="sxs-lookup"><span data-stu-id="4d7ae-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="4d7ae-134">Te klasy wyjątków będą łatwe do ponownego użycia z <xref:System.ServiceModel.FaultException%601> klasą WCF w celu wygenerowania nowego`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="4d7ae-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="4d7ae-135">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="4d7ae-135">Security</span></span>  
 <span data-ttu-id="4d7ae-136">Poniżej przedstawiono niektóre zalecenia dotyczące zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="4d7ae-137">Unikaj używania profilów ASP.NET 2,0, ponieważ użycie ich może ograniczyć użycie trybu integracji ASP.NET, jeśli usługa została zmigrowana do programu WCF.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="4d7ae-138">Unikaj używania list ACL do kontrolowania dostępu do usług, ponieważ usługi sieci Web ASP.NET obsługują listy ACL korzystające z Internet Information Services (IIS), WCF nie — ponieważ usługi sieci Web ASP.NET są zależne od usług IIS do hostingu, a usługa WCF nie musi być hostowana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="4d7ae-139">Należy rozważyć użycie dostawców roli ASP.NET 2,0 do autoryzacji dostępu do zasobów usługi.</span><span class="sxs-lookup"><span data-stu-id="4d7ae-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7ae-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d7ae-140">See also</span></span>

- [<span data-ttu-id="4d7ae-141">Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości</span><span class="sxs-lookup"><span data-stu-id="4d7ae-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](anticipating-adopting-the-wcf-easing-future-integration.md)
