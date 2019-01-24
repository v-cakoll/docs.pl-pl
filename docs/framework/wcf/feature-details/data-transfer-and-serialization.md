---
title: Transfer i serializacja danych
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 5192030fa2eda45431dd8a3765603d3081b93fa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595321"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="b2cd4-102">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="b2cd4-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="b2cd4-103">W systemie połączonych usług i klientów są zależne od wymiany danych, aby wykonać dowolne zadanie.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="b2cd4-104">Jako deweloper usługi lub klienta również należy zrozumieć, jak Windows Communication Foundation (WCF) obsługuje dane i serializacja danych w celu tworzenia aplikacji, które są wydajne i łatwa w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2cd4-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b2cd4-105">In This Section</span></span>  
 [<span data-ttu-id="b2cd4-106">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="b2cd4-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="b2cd4-107">W tym artykule opisano podstawowe pojęcia transferu danych w usługach.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="b2cd4-108">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="b2cd4-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="b2cd4-109">W tym artykule opisano, jakie dane zamówień są i jak tworzyć i używać ich.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="b2cd4-110">Serializator kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="b2cd4-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="b2cd4-111">W tym artykule opisano sposób wykonywania serializacji danych za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> klasy lub dowolnego rozszerzenia <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="b2cd4-112">Używanie klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b2cd4-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="b2cd4-113">Opisuje, jak i dlaczego warto używać <xref:System.Xml.Serialization.XmlSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="b2cd4-114">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="b2cd4-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="b2cd4-115">W tym artykule opisano, jak kontrakty komunikatów umożliwia szczegółową kontrolę komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="b2cd4-116">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="b2cd4-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="b2cd4-117">W tym artykule opisano, jak korzystać z funkcji klasy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="b2cd4-118">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="b2cd4-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="b2cd4-119">W tym artykule opisano, filtrowania, które umożliwia wstępne przetwarzanie komunikatów, na podstawie różnych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="b2cd4-120">Duże ilości danych i przesyłanie strumieniowe</span><span class="sxs-lookup"><span data-stu-id="b2cd4-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="b2cd4-121">W tym artykule opisano sposób wysyłania dużych bloków danych, takich jak plik binarny.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="b2cd4-122">Zagadnienia związane z zabezpieczeniami danych</span><span class="sxs-lookup"><span data-stu-id="b2cd4-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="b2cd4-123">W tym artykule opisano elementy, których trzeba pamiętać podczas programowania transfer i serializacja danych.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="b2cd4-124">Omówienie architektury transferu danych</span><span class="sxs-lookup"><span data-stu-id="b2cd4-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="b2cd4-125">Opisuje widok ogólnego projektu transferu danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="b2cd4-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b2cd4-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b2cd4-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="b2cd4-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b2cd4-127">Related Sections</span></span>  
 [<span data-ttu-id="b2cd4-128">Rozszerzanie koderów i serializatorów</span><span class="sxs-lookup"><span data-stu-id="b2cd4-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2cd4-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2cd4-129">See also</span></span>
- [<span data-ttu-id="b2cd4-130">Najlepsze rozwiązania: Przechowywanie wersji kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="b2cd4-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [<span data-ttu-id="b2cd4-131">Przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="b2cd4-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
