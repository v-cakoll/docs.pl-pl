---
title: Obsługa integracji AJAX i notacji JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 54942386bb4fb88e72a86b5e25f12cee4776a126
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625643"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="7decf-102">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="7decf-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="7decf-103">Windows Communication Foundation (WCF) obsługuje ASP.NET asynchronicznego języki JavaScript i XML (technologia AJAX) i formatu JavaScript Object Notation (JSON) w danych umożliwiają usługi WCF do udostępnienia operacje klientom AJAX.</span><span class="sxs-lookup"><span data-stu-id="7decf-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="7decf-104">Klienci AJAX są stron sieci Web, wykonywanie kodu JavaScript i uzyskiwania dostępu do tych usług WCF za pomocą żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="7decf-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="7decf-105">Tematy w tej sekcji zawierają informacje dotyczące tej pomocy technicznej i sposobie jego implementowania.</span><span class="sxs-lookup"><span data-stu-id="7decf-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="7decf-106">Aby dowiedzieć się więcej o technologii ASP.NET AJAX i integracji z programem ASP.NET 2.0, zobacz [omówienie technologii AJAX programu ASP.NET](https://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="7decf-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7decf-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7decf-107">In This Section</span></span>  
 [<span data-ttu-id="7decf-108">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7decf-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="7decf-109">W tym artykule opisano, jak usługi WCF mogą łączyć się z klientami AJAX przez dodanie odpowiednich punktów końcowych AJAX, albo za pośrednictwem konfiguracji lub przy użyciu usługi fabryka hostów, dostosowane do generowania hosta usługi, która automatycznie konfiguruje punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="7decf-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="7decf-110">Tworzenie usług AJAX WCF bez platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7decf-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="7decf-111">W tym artykule opisano sposób tworzenia usługi WCF bez za pomocą programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7decf-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="7decf-112">Obsługa formatu JSON i innych formatów transferowania danych</span><span class="sxs-lookup"><span data-stu-id="7decf-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="7decf-113">W tym artykule opisano obsługi formatu JSON, zwykle używane (zamiast XML) do obsługi komunikatów z usługami ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7decf-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="7decf-114">Instrukcje: Migrowanie usług internetowych platformy ASP.NET z włączoną obsługą technologii AJAX do programu WCF</span><span class="sxs-lookup"><span data-stu-id="7decf-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="7decf-115">W tym artykule opisano, jak przeprowadzić migrację usługi sieci Web platformy ASP.NET z obsługą technologii AJAX do usługi sieci WCF Web.</span><span class="sxs-lookup"><span data-stu-id="7decf-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7decf-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7decf-116">See also</span></span>
- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="7decf-117">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7decf-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
