---
title: 'Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: fd61528770b16b13430be3691aef19c1cc743e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="8d664-102">Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="8d664-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="8d664-103">Aby nawiązać połączenie i komunikować się z usługą Windows Communication Foundation (WCF), aplikacja klienta WCF musi mieć szczegóły adresu usługi, Konfiguracja powiązania i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8d664-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="8d664-104">Moniker usługi WCF zwykle uzyskuje kontrakt wymagane przez wcześniejsze rejestrację typów wymaganego atrybutu, ale może być przypadki, w którym nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8d664-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="8d664-105">Zamiast rejestracji moniker można uzyskać definicję kontraktu w formularzu sieci Web Services Definition Language (WSDL) dokumentu, za pośrednictwem `wsdl` parametru lub za pomocą wymiany metadanych, korzystając ze `mexAddress` parametr.</span><span class="sxs-lookup"><span data-stu-id="8d664-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="8d664-106">Dzięki temu scenariuszy, takich jak dystrybucji arkusz kalkulacyjny programu Excel, gdzie niektórych wartości komórki są obliczane przy użyciu interakcje usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8d664-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="8d664-107">W tym scenariuszu może nie być możliwe do zarejestrowania zestawu kontraktu usługi na wszystkich klientach, które może otworzyć dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8d664-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="8d664-108">`wsdl` Parametru lub `mexAddress` parametru zapewnia rozwiązanie niezależne.</span><span class="sxs-lookup"><span data-stu-id="8d664-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d664-109">Uwierzytelnianie wzajemne, należy użyć do ochrony przed żądań i odpowiedzi, modyfikowaniu lub fałszowania.</span><span class="sxs-lookup"><span data-stu-id="8d664-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="8d664-110">W szczególności jest ważna w przypadku klientów mieć pewność, że punkt końcowy wymiany metadanych, który odpowiada jest zamierzone zaufany.</span><span class="sxs-lookup"><span data-stu-id="8d664-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d664-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d664-111">Example</span></span>  
 <span data-ttu-id="8d664-112">W tym przykładzie pokazano sposób użycia moniker usługi z kontraktem MEX.</span><span class="sxs-lookup"><span data-stu-id="8d664-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="8d664-113">Usługi za pomocą następujących kontrakt jest narażony na wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="8d664-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="8d664-114">Aby utworzyć klienta WCF dla usługi zdalnej następujący ciąg monikera przykład można użyć.</span><span class="sxs-lookup"><span data-stu-id="8d664-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="8d664-115">Podczas wykonywania aplikacji klienckiej, klient wykonuje `WS-MetadataExchange` się za pomocą podanych `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="8d664-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="8d664-116">Może to zwrócić address, binding i szczegóły umowy wielu usług.</span><span class="sxs-lookup"><span data-stu-id="8d664-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="8d664-117">`address`, `contract`, `contractNamespace`, `binding` i `bindingNamespace` parametry są używane do identyfikowania usługi zamierzone.</span><span class="sxs-lookup"><span data-stu-id="8d664-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="8d664-118">Po dopasowane tych parametrów moniker konstruuje klienta WCF z definicję kontraktu odpowiednie, a następnie wywołań za pomocą klienta WCF, podobnie jak w przypadku typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8d664-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d664-119">Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwraca błąd informujący o tym "Nieprawidłowa składnia".</span><span class="sxs-lookup"><span data-stu-id="8d664-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="8d664-120">Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="8d664-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d664-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d664-121">See Also</span></span>  
 [<span data-ttu-id="8d664-122">Instrukcje: rejestrowanie i konfigurowanie monikera usługi</span><span class="sxs-lookup"><span data-stu-id="8d664-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
