---
title: Transfer i serializacja danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41357c9a039414ac692bac69337b2963d5c6b341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="ee0eb-102">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="ee0eb-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="ee0eb-103">W systemie połączonych usług i klientów są zależne od wymiany danych, wykonywać wszystkie zadania.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="ee0eb-104">Jako deweloper usługi lub klienta, należy również poznać sposób [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje dane i serializacja danych, aby można było utworzyć aplikacje, które są wydajne i łatwe w konserwacji.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-104">As a developer of a service or client, you must also understand how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee0eb-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ee0eb-105">In This Section</span></span>  
 [<span data-ttu-id="ee0eb-106">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="ee0eb-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="ee0eb-107">W tym artykule opisano podstawowe pojęcia transfer danych w usługach.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="ee0eb-108">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="ee0eb-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="ee0eb-109">W tym artykule opisano, jakie dane kontraktów są oraz sposobu tworzenia i korzystania z nich.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="ee0eb-110">Serializator kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="ee0eb-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="ee0eb-111">Opisuje sposób wykonywania serializacji danych za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> klasy lub przedłużenia <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="ee0eb-112">Przy użyciu klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ee0eb-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="ee0eb-113">Opisuje, jak i dlaczego używać <xref:System.Xml.Serialization.XmlSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="ee0eb-114">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="ee0eb-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="ee0eb-115">W tym artykule opisano, jak kontrakty komunikatu umożliwia szczegółową kontrolę wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="ee0eb-116">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="ee0eb-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="ee0eb-117">Opisuje sposób korzystania z funkcji klasy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="ee0eb-118">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="ee0eb-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="ee0eb-119">Opisuje filtrowania, które umożliwia przetwarzanie wstępne wiadomości na podstawie różnych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="ee0eb-120">Duże ilości danych i przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="ee0eb-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="ee0eb-121">Opisuje sposób wysyłania dużych bloków danych, takich jak plik binarny.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="ee0eb-122">Zagadnienia dotyczące zabezpieczeń dla danych</span><span class="sxs-lookup"><span data-stu-id="ee0eb-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="ee0eb-123">W tym artykule opisano elementy pod uwagę podczas programowania transfer i serializacja danych.</span><span class="sxs-lookup"><span data-stu-id="ee0eb-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="ee0eb-124">Omówienie architektury transferu danych</span><span class="sxs-lookup"><span data-stu-id="ee0eb-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="ee0eb-125">W tym artykule opisano widok ogólnego projektu transferu danych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee0eb-125">Describes a view of the overall design of data transfer in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ee0eb-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ee0eb-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="ee0eb-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ee0eb-127">Related Sections</span></span>  
 [<span data-ttu-id="ee0eb-128">Rozszerzanie koderów i serializatorów</span><span class="sxs-lookup"><span data-stu-id="ee0eb-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee0eb-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee0eb-129">See Also</span></span>  
 [<span data-ttu-id="ee0eb-130">Wskazówki: Przechowywanie wersji kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="ee0eb-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="ee0eb-131">Przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="ee0eb-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
