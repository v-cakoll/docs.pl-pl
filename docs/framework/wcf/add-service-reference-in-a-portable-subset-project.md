---
title: Dodawanie odwołania usługi w projekcie obsługującym podzestaw przenośny
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 764ce487d8f2673eb2c75f8cd05da4ccbae3c935
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320851"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="473ed-102">Dodawanie odwołania usługi w projekcie obsługującym podzestaw przenośny</span><span class="sxs-lookup"><span data-stu-id="473ed-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="473ed-103">Przenośne projekty podzestawów umożliwiają programistom zestawu .NET utrzymywanie jednego drzewa źródłowego i systemu kompilacji przy zachowaniu obsługi wielu implementacji platformy .NET (Desktop, Silverlight, Windows Phone i XBOX).</span><span class="sxs-lookup"><span data-stu-id="473ed-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="473ed-104">Przenośne projekty podzestawów odwołują się tylko do przenośnych bibliotek platformy .NET, które są zestawami programu .NET Framework, które mogą być używane w dowolnej implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="473ed-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="473ed-105">Szczegóły Dodaj odwołanie do usługi</span><span class="sxs-lookup"><span data-stu-id="473ed-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="473ed-106">Podczas dodawania odwołania do usługi w projekcie podzestawu przenośnego są wymuszane następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="473ed-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="473ed-107">W przypadku <xref:System.Xml.Serialization.XmlSerializer> dozwolone są tylko kodowania literałów.</span><span class="sxs-lookup"><span data-stu-id="473ed-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="473ed-108">Kodowanie protokołu SOAP generuje błąd podczas importowania.</span><span class="sxs-lookup"><span data-stu-id="473ed-108">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="473ed-109">W przypadku usług korzystających z scenariuszy <xref:System.Runtime.Serialization.DataContractSerializer> jest dostarczany Surogat kontraktu danych w celu zapewnienia, że ponownie używane typy są dostępne tylko z podzestawem przenośnym.</span><span class="sxs-lookup"><span data-stu-id="473ed-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="473ed-110">Punkty końcowe, które opierają się na powiązaniach, nie są obsługiwane w przenośnych bibliotekach (wszystkie powiązania z wyjątkiem <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> bez przepływu transakcji, sesji niezawodnych lub kodowania MTOM oraz równoważne powiązania niestandardowe) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="473ed-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="473ed-111">Nagłówki wiadomości są usuwane ze wszystkich opisów komunikatów we wszystkich operacjach przed zaimportowaniem.</span><span class="sxs-lookup"><span data-stu-id="473ed-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="473ed-112">Atrybuty inne niż przenośne <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute> i <xref:System.ServiceModel.TransactionFlowAttribute> są usuwane z wygenerowanego kodu serwera proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="473ed-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="473ed-113">Właściwości nieprzenośne ProtectionLevel, SessionMode, isisinitiating, iskończona są usuwane z <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute> i <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="473ed-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="473ed-114">Wszystkie operacje usługi są generowane jako operacje asynchroniczne na serwerze proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="473ed-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="473ed-115">Wygenerowane konstruktory klienta, które używają typów nieprzenośnych, są usuwane.</span><span class="sxs-lookup"><span data-stu-id="473ed-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="473ed-116">Wystąpienie <xref:System.Net.CookieContainer> jest uwidocznione na wygenerowanym kliencie.</span><span class="sxs-lookup"><span data-stu-id="473ed-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="473ed-117">W górnej części pliku zostanie wstawiony komentarz identyfikujący zestaw i wersję generatora kodu: `// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="473ed-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="473ed-118">Interfejs <xref:System.Runtime.Serialization.ISerializable> nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="473ed-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="473ed-119">Powiązania net. TCP i PollingDuplex nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="473ed-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="473ed-120">@No__t-0 będzie zawsze używana w przypadku błędów.</span><span class="sxs-lookup"><span data-stu-id="473ed-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="473ed-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> nie jest obsługiwane w projektach podzestawu przenośnych.</span><span class="sxs-lookup"><span data-stu-id="473ed-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473ed-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="473ed-122">See also</span></span>

- [<span data-ttu-id="473ed-123">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="473ed-123">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="473ed-124">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="473ed-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
