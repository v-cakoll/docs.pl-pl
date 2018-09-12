---
title: Dodawanie odwołania usługi w projekcie obsługującym podzestaw przenośny
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: efe95a326e7c13237c7d2d74888c85bf919ed287
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44507779"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="4afb7-102">Dodawanie odwołania usługi w projekcie obsługującym podzestaw przenośny</span><span class="sxs-lookup"><span data-stu-id="4afb7-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="4afb7-103">Projekty obsługującym podzestaw przenośny umożliwiają deweloperom zestawu .NET do utrzymywania drzewa pojedyncze źródło i systemu kompilacji, nadal obsługując wiele implementacji .NET (pulpitu, Silverlight, Windows Phone i XBOX).</span><span class="sxs-lookup"><span data-stu-id="4afb7-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="4afb7-104">Projekty obsługującym podzestaw przenośny tylko odwołania do bibliotek przenośnych platformy .NET, będące zestaw .NET framework, używanym w implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="4afb7-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="4afb7-105">Dodaj szczegóły usługi</span><span class="sxs-lookup"><span data-stu-id="4afb7-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="4afb7-106">Podczas dodawania odwołania do usługi w projekcie obsługującym podzestaw przenośny obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4afb7-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="4afb7-107">Aby uzyskać <xref:System.Xml.Serialization.XmlSerializer>, dozwolone są tylko literał kodowania.</span><span class="sxs-lookup"><span data-stu-id="4afb7-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="4afb7-108">Kodowania SOAP generuje błąd podczas importowania.</span><span class="sxs-lookup"><span data-stu-id="4afb7-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="4afb7-109">Dla usługi używające <xref:System.Runtime.Serialization.DataContractSerializer> scenariuszy, danych zastępcza Umowa znajduje się w celu zapewnienia, że typy ponownie pochodzić tylko z obsługującym podzestaw przenośny.</span><span class="sxs-lookup"><span data-stu-id="4afb7-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="4afb7-110">Punkty końcowe, które zależą od powiązania nie są obsługiwane w przenośnych bibliotekach (wszystkie powiązania z wyjątkiem <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> bez przepływu transakcji, niezawodnej sesji lub kodowanie MTOM i powiązań niestandardowych równoważne) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="4afb7-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="4afb7-111">Nagłówki wiadomości są usuwane z wszystkie opisy wiadomości we wszystkich operacjach przed zaimportowaniem.</span><span class="sxs-lookup"><span data-stu-id="4afb7-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="4afb7-112">Atrybuty nieprzenośne <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, i <xref:System.ServiceModel.TransactionFlowAttribute> są usuwane z kodu serwera proxy wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="4afb7-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="4afb7-113">Nieprzenośne właściwości ProtectionLevel, SessionMode, IsInitiating i IsTerminating są usuwane z <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, i <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4afb7-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="4afb7-114">Wszystkie operacje usługi są generowane jako operacji asynchronicznych na serwerze proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="4afb7-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="4afb7-115">Konstruktor wygenerowanego klienta, który używa typów nieprzenośne są usuwane.</span><span class="sxs-lookup"><span data-stu-id="4afb7-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="4afb7-116">A <xref:System.Net.CookieContainer> wystąpienia jest uwidaczniany w wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="4afb7-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="4afb7-117">Komentarz zostanie wstawione w górnej części pliku zestawu i wersję generatora kodu:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="4afb7-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="4afb7-118"><xref:System.Runtime.Serialization.ISerializable> Interfejs nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="4afb7-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="4afb7-119">Powiązania Net.Tcp i PollingDuplex nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4afb7-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="4afb7-120"><xref:System.Runtime.Serialization.DataContractSerializer> Będzie zawsze używana dla błędów.</span><span class="sxs-lookup"><span data-stu-id="4afb7-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="4afb7-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> nie jest obsługiwane w projektach obsługującym podzestaw przenośny.</span><span class="sxs-lookup"><span data-stu-id="4afb7-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afb7-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4afb7-122">See Also</span></span>  
 [<span data-ttu-id="4afb7-123">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="4afb7-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="4afb7-124">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="4afb7-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
