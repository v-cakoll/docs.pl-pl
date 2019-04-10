---
title: 'Instrukcje: używanie krótkiej nazwy programu Windows Communication Foundation bez rejestracji'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: be4798663d0b39301ec496df45a4a7a5bf9c88e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203980"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="46bab-102">Instrukcje: używanie krótkiej nazwy programu Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="46bab-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="46bab-103">Aby nawiązać połączenie i komunikować się z usługą Windows Communication Foundation (WCF), aplikacja klienta WCF musi mieć adres usługi, Konfiguracja powiązania i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="46bab-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="46bab-104">Monikera programu WCF zwykle uzyskuje kontrakt wymagane przez wcześniejsze rejestrację typów wymaganego atrybutu, ale może być przypadki, w którym nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="46bab-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="46bab-105">Zamiast rejestracji, moniker można uzyskać definicję kontraktu w postaci dokumentów sieci Web Services Definition Language (WSDL), za pośrednictwem `wsdl` parametru lub za pośrednictwem wymiany metadanych, korzystając ze `mexAddress` parametr.</span><span class="sxs-lookup"><span data-stu-id="46bab-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="46bab-106">Umożliwia to obsługę scenariuszy, takich jak dystrybucja arkusz kalkulacyjny programu Excel, gdzie niektóre komórki wartościami są obliczane za pośrednictwem interakcje usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="46bab-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="46bab-107">W tym scenariuszu może być nie można zarejestrować zestawu kontraktu usługi na wszystkich klientach, które może otworzyć dokumentu.</span><span class="sxs-lookup"><span data-stu-id="46bab-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="46bab-108">`wsdl` Parametru lub `mexAddress` parametr umożliwia samodzielne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="46bab-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46bab-109">Wzajemnego uwierzytelniania musi być używana do ochrony przed żądań i odpowiedzi, modyfikowaniu lub fałszowanie adresów.</span><span class="sxs-lookup"><span data-stu-id="46bab-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="46bab-110">Ściślej mówiąc jest ważne dla klientów mieć pewność, że punkt końcowy wymiany metadanych, który odpowiada jest zamierzony zaufany.</span><span class="sxs-lookup"><span data-stu-id="46bab-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46bab-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="46bab-111">Example</span></span>  
 <span data-ttu-id="46bab-112">Ten przykład przedstawia użycie monikera za pomocą kontraktu wymiany Metadanych.</span><span class="sxs-lookup"><span data-stu-id="46bab-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="46bab-113">Usługi za pomocą następujących kontraktu jest uwidaczniany za pomocą wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="46bab-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
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
  
 <span data-ttu-id="46bab-114">Aby utworzyć klienta WCF usługi zdalnej następujący ciąg monikera przykład można użyć.</span><span class="sxs-lookup"><span data-stu-id="46bab-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="46bab-115">Podczas wykonywania aplikacji klienckiej, klient wykonuje `WS-MetadataExchange` z dostępnego `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="46bab-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="46bab-116">To może zwrócić adres, powiązania i podrobnosti o kontraktu dla wielu usług.</span><span class="sxs-lookup"><span data-stu-id="46bab-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="46bab-117">`address`, `contract`, `contractNamespace`, `binding` i `bindingNamespace` parametry są używane do identyfikowania usługi zamierzone.</span><span class="sxs-lookup"><span data-stu-id="46bab-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="46bab-118">Po dopasowane tych parametrów moniker tworzy klienta programu WCF za pomocą definicję kontraktu odpowiednie, a następnie wywołań za pomocą klienta WCF, podobnie jak w przypadku wpisane kontraktu.</span><span class="sxs-lookup"><span data-stu-id="46bab-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46bab-119">Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwraca błąd informujący o "Nieprawidłowa składnia".</span><span class="sxs-lookup"><span data-stu-id="46bab-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="46bab-120">Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="46bab-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46bab-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46bab-121">See also</span></span>

- [<span data-ttu-id="46bab-122">Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi</span><span class="sxs-lookup"><span data-stu-id="46bab-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
