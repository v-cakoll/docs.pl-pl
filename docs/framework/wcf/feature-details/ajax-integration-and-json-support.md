---
title: Obsługa integracji AJAX i notacji JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 0b392044db3fbc926bf77ac305ece294880216d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="07c3e-102">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="07c3e-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="07c3e-103">Usługi WCF do udostępnienia operacji klientom AJAX Zezwalaj na obsługę Windows Communication Foundation (WCF) ASP.NET asynchronicznego JavaScript i XML (AJAX) i format danych JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="07c3e-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="07c3e-104">Klienci AJAX są stron sieci Web wykonywanie kodu JavaScript i uzyskiwania dostępu do tych usług WCF za pomocą żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="07c3e-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="07c3e-105">Tematy w tej sekcji zawierają informacje dotyczące tej obsługi i wdrożenie go.</span><span class="sxs-lookup"><span data-stu-id="07c3e-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="07c3e-106">Więcej informacji na temat środowiska ASP.NET AJAX i jego integracji z programem ASP.NET 2.0, zobacz [ASP.NET AJAX omówienie](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="07c3e-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07c3e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="07c3e-107">In This Section</span></span>  
 [<span data-ttu-id="07c3e-108">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="07c3e-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="07c3e-109">W tym artykule opisano, jak usługa WCF można widoczne dla klientów AJAX, dodając odpowiednie punktu końcowego AJAX albo za pomocą konfiguracji lub za pomocą fabryki hostów usług, dostosowane do generowania hosta usługi, która automatycznie konfiguruje punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="07c3e-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="07c3e-110">Tworzenie usług AJAX WCF bez platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="07c3e-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="07c3e-111">Opisuje sposób tworzenia usługi WCF bez użycia platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="07c3e-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="07c3e-112">Obsługa formatu JSON i innych formatów transferowania danych</span><span class="sxs-lookup"><span data-stu-id="07c3e-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="07c3e-113">W tym artykule opisano obsługę formatu JSON, zwykle (zamiast XML) używany do obsługi wiadomości z usługami ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="07c3e-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="07c3e-114">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="07c3e-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="07c3e-115">Opisano sposób migracji usługi sieci Web ASP.NET włączoną obsługą technologii AJAX do usługi sieci WCF Web.</span><span class="sxs-lookup"><span data-stu-id="07c3e-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c3e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07c3e-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="07c3e-117">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="07c3e-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
