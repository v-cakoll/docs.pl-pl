---
title: Formaty metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a><span data-ttu-id="2da95-102">Formaty metadanych</span><span class="sxs-lookup"><span data-stu-id="2da95-102">Metadata Formats</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2da95-103">obsługuje formaty metadanych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2da95-103"> supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="2da95-104">Specyfikacje metadanych i użycia</span><span class="sxs-lookup"><span data-stu-id="2da95-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="2da95-105">Protokół</span><span class="sxs-lookup"><span data-stu-id="2da95-105">Protocol</span></span>|<span data-ttu-id="2da95-106">Specyfikacja i użycia</span><span class="sxs-lookup"><span data-stu-id="2da95-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="2da95-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="2da95-107">WSDL 1.1</span></span>|[<span data-ttu-id="2da95-108">Web Services Description Language (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="2da95-108">Web Services Description Language (WSDL) 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2da95-109">używa usługi sieci Web Services Description Language (WSDL) do opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="2da95-109"> uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="2da95-110">schemat XML</span><span class="sxs-lookup"><span data-stu-id="2da95-110">XML Schema</span></span>|<span data-ttu-id="2da95-111">[XML schematu część 2: Wydanie drugie typów danych](http://go.microsoft.com/fwlink/?LinkId=94861) i [część schematu XML 1: struktury wydanie drugie](http://go.microsoft.com/fwlink/?LinkId=94862)</span><span class="sxs-lookup"><span data-stu-id="2da95-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) and [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span></span><br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2da95-112">używa schematu XML opisujący typów danych używanych w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2da95-112"> uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="2da95-113">Zasady protokołu WS</span><span class="sxs-lookup"><span data-stu-id="2da95-113">WS Policy</span></span>|[<span data-ttu-id="2da95-114">Zasady usługi sieci Web 1.2 - Framework (WS-Policy)</span><span class="sxs-lookup"><span data-stu-id="2da95-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [<span data-ttu-id="2da95-115">Zasady usługi sieci Web w wersji 1.5 — Framework</span><span class="sxs-lookup"><span data-stu-id="2da95-115">Web Services Policy 1.5 - Framework</span></span>](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2da95-116">używa 1.2 WS-Policy lub specyfikacji 1,5 z potwierdzeniami specyficznego dla domeny do opisu usługi wymagań i możliwości.</span><span class="sxs-lookup"><span data-stu-id="2da95-116"> uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="2da95-117">Załączniki polityki WS</span><span class="sxs-lookup"><span data-stu-id="2da95-117">WS Policy Attachments</span></span>|[<span data-ttu-id="2da95-118">Zasady usługi sieci Web 1.2 - załącznika (WS-PolicyAttachment)</span><span class="sxs-lookup"><span data-stu-id="2da95-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2da95-119">implementuje usługi WS-Policy załączników do podłączenia zasad wyrażenia w różnych zakresów w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="2da95-119"> implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="2da95-120">Wymiany metadanych WS</span><span class="sxs-lookup"><span data-stu-id="2da95-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="2da95-121">Wymiany metadanych usługi sieci Web (WS-MetadataExchange) w wersji 1.1</span><span class="sxs-lookup"><span data-stu-id="2da95-121">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2da95-122">implementuje usługi WS-MetadataExchange, można pobrać schematu XML, WSDL i WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="2da95-122"> implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="2da95-123">Powiązanie WSDL adresowania WS</span><span class="sxs-lookup"><span data-stu-id="2da95-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="2da95-124">Usługi sieci Web adresowanie 1.0 - Powiązanie WSDL</span><span class="sxs-lookup"><span data-stu-id="2da95-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2da95-125">implementuje usługi WS-Addressing Powiązanie WSDL dołączyć informacje adresowania w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="2da95-125"> implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2da95-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2da95-126">See Also</span></span>  
 [<span data-ttu-id="2da95-127">Protokoły obsługiwane przez wiązania współdziałania udostępnione przez System usług sieci Web</span><span class="sxs-lookup"><span data-stu-id="2da95-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [<span data-ttu-id="2da95-128">WSDL i zasady</span><span class="sxs-lookup"><span data-stu-id="2da95-128">WSDL and Policy</span></span>](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
