---
title: Obsługa integracji AJAX i notacji JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 3054c3c6faa8dfe621c706d8df031c23d497da0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576515"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="6404d-102">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="6404d-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="6404d-103">Obsługa Windows Communication Foundation (WCF) dla ASP.NET asynchronicznego języka JavaScript i XML (AJAX) oraz formatu danych JavaScript Object Notation (JSON) umożliwia usługom WCF udostępnianie operacji klientom AJAX.</span><span class="sxs-lookup"><span data-stu-id="6404d-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="6404d-104">Klienci AJAX są stronami sieci Web, w których uruchomiono kod JavaScript i uzyskują dostęp do tych usług WCF przy użyciu żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="6404d-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="6404d-105">Tematy w tej sekcji zawierają informacje o tej pomocy technicznej i sposobach ich implementacji.</span><span class="sxs-lookup"><span data-stu-id="6404d-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="6404d-106">Aby uzyskać więcej informacji na temat ASP.NET AJAX i integracji z ASP.NET 2,0, zobacz [ASP.NET AJAX — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6404d-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6404d-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6404d-107">In This Section</span></span>  
 [<span data-ttu-id="6404d-108">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6404d-108">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="6404d-109">Opisuje, w jaki sposób można uwidocznić usługę WCF klientom AJAX, dodając odpowiedni punkt końcowy AJAX przez konfigurację lub przy użyciu fabryki hosta usługi dostosowanej do wygenerowania hosta usługi, który automatycznie konfiguruje punkt końcowy AJAX.</span><span class="sxs-lookup"><span data-stu-id="6404d-109">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="6404d-110">Tworzenie usług AJAX WCF bez platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6404d-110">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="6404d-111">Zawiera opis sposobu tworzenia usługi WCF bez używania ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6404d-111">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="6404d-112">Obsługa formatu JSON i innych formatów transferowania danych</span><span class="sxs-lookup"><span data-stu-id="6404d-112">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="6404d-113">W tym artykule opisano obsługę formatu JSON, który zwykle jest używany (zamiast XML) do obsługi komunikatów w usłudze ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6404d-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="6404d-114">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="6404d-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="6404d-115">Opisuje sposób migrowania usługi sieci Web ASP.NET z włączoną obsługą technologii AJAX do usługi sieci Web programu WCF.</span><span class="sxs-lookup"><span data-stu-id="6404d-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6404d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6404d-116">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="6404d-117">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="6404d-117">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
