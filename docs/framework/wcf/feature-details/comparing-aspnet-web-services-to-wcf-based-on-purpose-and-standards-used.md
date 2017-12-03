---
title: "Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3fec18cb93486dfe9d2b09582ad263d19b00617
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a><span data-ttu-id="a09e8-102">Porównanie usług sieci Web platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów</span><span class="sxs-lookup"><span data-stu-id="a09e8-102">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>
<span data-ttu-id="a09e8-103">Usługi sieci Web platformy ASP.NET został opracowany do tworzenia aplikacji, które wysyłać i odbierać wiadomości przy użyciu obiektu dostępu protokołu SOAP (Simple) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a09e8-103">ASP.NET Web services was developed for building applications that send and receive messages by using the Simple Object Access Protocol (SOAP) over HTTP.</span></span> <span data-ttu-id="a09e8-104">Struktura komunikaty mogą być definiowane przy użyciu schematu XML, a narzędzie jest dostarczany w celu ułatwienia serializacji komunikatów do i z obiektami środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a09e8-104">The structure of the messages can be defined using an XML Schema, and a tool is provided to facilitate serializing the messages to and from .NET Framework objects.</span></span> <span data-ttu-id="a09e8-105">Technologia może automatycznie generować metadane do opisu usługi sieci Web w sieci Web Services Description Language (WSDL), a drugi narzędzie jest dostępne w celu generowania klientów dla usług sieci Web z pliku WSDL.</span><span class="sxs-lookup"><span data-stu-id="a09e8-105">The technology can automatically generate metadata to describe Web services in the Web Services Description Language (WSDL), and a second tool is provided for generating clients for Web services from the WSDL.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a09e8-106">jest dotyczące włączania aplikacji .NET Framework do wymiany wiadomości z innym podmiotom oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a09e8-106"> is for enabling .NET Framework applications to exchange messages with other software entities.</span></span> <span data-ttu-id="a09e8-107">Domyślnie jest używany protokół SOAP, ale komunikaty można w dowolnym formacie i przekazywanych przy użyciu dowolnego protokołu transportu.</span><span class="sxs-lookup"><span data-stu-id="a09e8-107">SOAP is used by default, but the messages can be in any format, and conveyed by using any transport protocol.</span></span> <span data-ttu-id="a09e8-108">Struktura komunikaty mogą być definiowane przy użyciu schematu XML, a istnieją różne opcje dla serializacji komunikatów do i z obiektami środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a09e8-108">The structure of the messages can be defined using an XML Schema, and there are various options for serializing the messages to and from .NET Framework objects.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a09e8-109">może automatycznie generować metadane do opisywania aplikacje utworzone przy użyciu technologii w języku WSDL, a także udostępnia narzędzia generowania klientów dla tych aplikacji z pliku WSDL.</span><span class="sxs-lookup"><span data-stu-id="a09e8-109"> can automatically generate metadata to describe applications built using the technology in WSDL, and it also provides a tool for generating clients for those applications from the WSDL.</span></span>  
  
 <span data-ttu-id="a09e8-110">Standardów obsługiwanych przez usługi sieci Web ASP.NET są udokumentowane w artykule [XML sieci Web usług utworzone za pomocą programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span><span class="sxs-lookup"><span data-stu-id="a09e8-110">The standards supported by ASP.NET Web services are documented in [XML Web Services Created Using ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span></span> <span data-ttu-id="a09e8-111">Bardziej rozległych listę standardów obsługiwanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znajduje się w [sieci Web usług protokoły obsługiwane przez wiązania współdziałania System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a09e8-111">The more extensive list of standards supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are listed at [Web Services Protocols Supported by System-Provided Interoperability Bindings](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09e8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a09e8-112">See Also</span></span>  
 [<span data-ttu-id="a09e8-113">Porównanie usług sieci Web ASP.NET do programu WCF na podstawie procesów programistycznych</span><span class="sxs-lookup"><span data-stu-id="a09e8-113">Comparing ASP.NET Web Services to WCF Based on Development</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
