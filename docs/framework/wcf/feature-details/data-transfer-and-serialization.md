---
title: Transfer i serializacja danych
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593493"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="fe665-102">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="fe665-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="fe665-103">W połączonym systemie usługi i klienci zależą od wymiany danych w celu wykonania dowolnego zadania.</span><span class="sxs-lookup"><span data-stu-id="fe665-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="fe665-104">Jako deweloper usługi lub klienta należy również zrozumieć, w jaki sposób Windows Communication Foundation (WCF) obsługuje dane i serializacji danych w celu tworzenia aplikacji, które są wydajne i łatwe w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="fe665-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe665-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fe665-105">In This Section</span></span>  
 [<span data-ttu-id="fe665-106">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="fe665-106">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="fe665-107">Zawiera opis podstawowych pojęć związanych z transferem danych w usługach.</span><span class="sxs-lookup"><span data-stu-id="fe665-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="fe665-108">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="fe665-108">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="fe665-109">Zawiera opis umów dotyczących danych i sposobu ich tworzenia i używania.</span><span class="sxs-lookup"><span data-stu-id="fe665-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="fe665-110">Serializator kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="fe665-110">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="fe665-111">Opisuje, w jaki sposób wykonać serializacji danych z <xref:System.Runtime.Serialization.DataContractSerializer> klasą lub dowolnym rozszerzeniem <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="fe665-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="fe665-112">Używanie klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="fe665-112">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="fe665-113">Opisuje, jak i dlaczego należy używać <xref:System.Xml.Serialization.XmlSerializer> klasy, alternatywy dla <xref:System.Runtime.Serialization.DataContractSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="fe665-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="fe665-114">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="fe665-114">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="fe665-115">Opisuje sposób, w jaki kontrakty komunikatów umożliwiają kontrolę nad komunikatami protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="fe665-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="fe665-116">Używanie klasy Message</span><span class="sxs-lookup"><span data-stu-id="fe665-116">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="fe665-117">Opisuje sposób korzystania z funkcji klasy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fe665-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="fe665-118">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="fe665-118">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="fe665-119">Opisuje filtrowanie, które umożliwia wstępne przetwarzanie wiadomości na podstawie różnych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="fe665-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="fe665-120">Duże ilości danych i przesyłanie strumieniowe</span><span class="sxs-lookup"><span data-stu-id="fe665-120">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="fe665-121">Opisuje sposób wysyłania dużego bloku danych, takiego jak plik binarny.</span><span class="sxs-lookup"><span data-stu-id="fe665-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="fe665-122">Zagadnienia związane z zabezpieczeniami danych</span><span class="sxs-lookup"><span data-stu-id="fe665-122">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="fe665-123">Opisuje elementy, które mają być świadome podczas programowania transferu i serializacji danych.</span><span class="sxs-lookup"><span data-stu-id="fe665-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="fe665-124">Omówienie architektury transferu danych</span><span class="sxs-lookup"><span data-stu-id="fe665-124">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="fe665-125">Opisuje widok ogólnego projektu transferu danych w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="fe665-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fe665-126">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="fe665-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="fe665-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fe665-127">Related Sections</span></span>  
 [<span data-ttu-id="fe665-128">Rozszerzanie koderów i serializatorów</span><span class="sxs-lookup"><span data-stu-id="fe665-128">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="fe665-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe665-129">See also</span></span>

- [<span data-ttu-id="fe665-130">Najlepsze rozwiązania: przechowywanie wersji kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="fe665-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="fe665-131">Przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="fe665-131">Service Versioning</span></span>](../service-versioning.md)
