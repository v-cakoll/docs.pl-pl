---
title: Obsługa integracji AJAX i notacji JSON
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0d62da8cf67fb8f996f341018c39146b51e308c3
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="2549e-102">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="2549e-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="2549e-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Obsługę asynchronicznych języka JavaScript ASP.NET i XML (AJAX) i format danych JavaScript Object Notation (JSON) pozwalają [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług do udostępnienia operacji klientom AJAX.</span><span class="sxs-lookup"><span data-stu-id="2549e-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="2549e-104">Klienci AJAX są stron sieci Web wykonywanie kodu JavaScript i uzyskiwania dostępu do tych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług za pomocą żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="2549e-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="2549e-105">Tematy w tej sekcji zawierają informacje dotyczące tej obsługi i wdrożenie go.</span><span class="sxs-lookup"><span data-stu-id="2549e-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="2549e-106">Więcej informacji na temat środowiska ASP.NET AJAX i jego integracji z programem ASP.NET 2.0, zobacz [ASP.NET AJAX omówienie](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="2549e-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2549e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2549e-107">In This Section</span></span>  
 [<span data-ttu-id="2549e-108">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2549e-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="2549e-109">Opisuje sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi można udostępnić klientom AJAX, dodając odpowiednie punktu końcowego AJAX za pomocą konfiguracji lub przy użyciu fabryki hostów usług dostosowane do generowania hosta usługi, która automatycznie konfiguruje punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="2549e-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="2549e-110">Tworzenie usług AJAX WCF bez platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2549e-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="2549e-111">Opisuje sposób tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi bez użycia platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2549e-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="2549e-112">Obsługa formatu JSON i innych formatów transferowania danych</span><span class="sxs-lookup"><span data-stu-id="2549e-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="2549e-113">W tym artykule opisano obsługę formatu JSON, zwykle (zamiast XML) używany do obsługi wiadomości z usługami ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2549e-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="2549e-114">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="2549e-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="2549e-115">Opisano sposób migracji usługi sieci Web ASP.NET włączoną obsługą technologii AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2549e-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2549e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2549e-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="2549e-117">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="2549e-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
