---
title: "Biblioteka klienta usługi danych WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e8f5626ab7439b34377ba0200fd232c41017652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="15a7a-102">Biblioteka klienta usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="15a7a-102">WCF Data Services Client Library</span></span>
<span data-ttu-id="15a7a-103">Wszelkie aplikacje mogą współdziałać z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]— na podstawie danych usługi, jeśli może wysłać żądania HTTP i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych zwracanych usługi danych.</span><span class="sxs-lookup"><span data-stu-id="15a7a-103">Any application can interact with an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-based data service if it can send an HTTP request and process the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that a data service returns.</span></span> <span data-ttu-id="15a7a-104">Współdziałanie ten umożliwia dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usług z szerokim aplikacje korzystające z zakresu sieci Web.</span><span class="sxs-lookup"><span data-stu-id="15a7a-104">This interoperability enables you to access [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based services from a broad range of Web-enabled applications.</span></span> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="15a7a-105">zawiera biblioteki klienta, które oferują więcej możliwości programowania, gdy zostaną zużyte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła .NET Framework lub aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="15a7a-105"> includes client libraries that provide a richer programming experience when you consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="15a7a-106">Dwie klasy głównym biblioteki klienta są <xref:System.Data.Services.Client.DataServiceContext> klasy i <xref:System.Data.Services.Client.DataServiceQuery%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="15a7a-106">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="15a7a-107"><xref:System.Data.Services.Client.DataServiceContext> Klasa hermetyzuje operacje, które są obsługiwane z usługą określone dane.</span><span class="sxs-lookup"><span data-stu-id="15a7a-107">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="15a7a-108">Mimo że [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi są bezstanowych, kontekst nie jest.</span><span class="sxs-lookup"><span data-stu-id="15a7a-108">Although [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] services are stateless, the context is not.</span></span> <span data-ttu-id="15a7a-109">W związku z tym można użyć <xref:System.Data.Services.Client.DataServiceContext> klasy do zarządzania stanem na kliencie między interakcji z usługą danych, aby zapewnić obsługę funkcji, takich jak zarządzanie zmianami.</span><span class="sxs-lookup"><span data-stu-id="15a7a-109">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="15a7a-110">Ta klasa również zarządza tożsamości i śledzi zmiany.</span><span class="sxs-lookup"><span data-stu-id="15a7a-110">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="15a7a-111"><xref:System.Data.Services.Client.DataServiceQuery%601> Klasa reprezentuje zapytanie pod kątem określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="15a7a-111">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="15a7a-112">W tej sekcji opisano, jak przy użyciu bibliotek klienta dostępu i zmiany danych z aplikacją kliencką programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15a7a-112">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="15a7a-113">Aby uzyskać więcej informacji o sposobie używania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta oparte na technologii Silverlight aplikacji, zobacz [usługi danych WCF (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016).</span><span class="sxs-lookup"><span data-stu-id="15a7a-113">For more information about how to use the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016).</span></span> <span data-ttu-id="15a7a-114">Dostępne są inne biblioteki klienta umożliwiające korzystanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w innych rodzajów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="15a7a-114">Other client libraries are available that enable you to consume an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in other kinds of applications.</span></span> <span data-ttu-id="15a7a-115">Aby uzyskać więcej informacji, zobacz [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).</span><span class="sxs-lookup"><span data-stu-id="15a7a-115">For more information, see the [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15a7a-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="15a7a-116">In This Section</span></span>  
 [<span data-ttu-id="15a7a-117">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="15a7a-117">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="15a7a-118">Opisuje sposób generowania biblioteki klienta i klasy usługi danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="15a7a-118">Describes how to generate a client library and client data service classes that are based on [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="15a7a-119">Wykonywanie zapytań do usługi danych</span><span class="sxs-lookup"><span data-stu-id="15a7a-119">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="15a7a-120">Opisuje sposób tworzenia zapytań za pomocą biblioteki klienta usługi danych z aplikacji opartych na programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15a7a-120">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="15a7a-121">Ładowanie odroczonej zawartości</span><span class="sxs-lookup"><span data-stu-id="15a7a-121">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="15a7a-122">Opisuje sposób załadować dodatkowej zawartości nie jest uwzględniony w odpowiedzi na zapytanie początkowej.</span><span class="sxs-lookup"><span data-stu-id="15a7a-122">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="15a7a-123">Aktualizacja usługi danych</span><span class="sxs-lookup"><span data-stu-id="15a7a-123">Updating the Data Service</span></span>](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="15a7a-124">Opisuje sposób tworzenia, modyfikowania i usuwania jednostki i relacje za pomocą biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="15a7a-124">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="15a7a-125">Operacje asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="15a7a-125">Asynchronous Operations</span></span>](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="15a7a-126">Zawiera opis funkcji podana przez klienta biblioteki do pracy z usługą danych w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="15a7a-126">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="15a7a-127">Operacje przetwarzania wsadowego</span><span class="sxs-lookup"><span data-stu-id="15a7a-127">Batching Operations</span></span>](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 <span data-ttu-id="15a7a-128">Opisuje sposób wysyłania wielu żądań do usługi danych w jednej serii za pomocą biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="15a7a-128">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="15a7a-129">Wiązanie danych do kontrolki</span><span class="sxs-lookup"><span data-stu-id="15a7a-129">Binding Data to Controls</span></span>](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="15a7a-130">Opisuje sposób wiązania kontrolki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zwrócony przez usługę danych źródła danych.</span><span class="sxs-lookup"><span data-stu-id="15a7a-130">Describes how to bind controls to a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="15a7a-131">Wywołania operacji usługi</span><span class="sxs-lookup"><span data-stu-id="15a7a-131">Calling Service Operations</span></span>](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="15a7a-132">Opisuje sposób korzystania z biblioteki klienta do wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="15a7a-132">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="15a7a-133">Zarządzanie kontekstem usługi danych</span><span class="sxs-lookup"><span data-stu-id="15a7a-133">Managing the Data Service Context</span></span>](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="15a7a-134">Opisuje opcje zarządzania zachowanie biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="15a7a-134">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="15a7a-135">Praca z danymi binarnymi</span><span class="sxs-lookup"><span data-stu-id="15a7a-135">Working with Binary Data</span></span>](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="15a7a-136">Opisuje sposób dostępu i zmiany danych binarnych zwrócony przez usługę do dane jako strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="15a7a-136">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a7a-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a7a-137">See Also</span></span>  
 [<span data-ttu-id="15a7a-138">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="15a7a-138">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="15a7a-139">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="15a7a-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
