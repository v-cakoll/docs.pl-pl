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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29ca4041e24a99546dfb665b0ce9e695732442d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="data-transfer-and-serialization"></a>Transfer i serializacja danych
W systemie połączonych usług i klientów są zależne od wymiany danych, wykonywać wszystkie zadania. Jako deweloper usługi lub klienta, należy również poznać sposób [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje dane i serializacja danych, aby można było utworzyć aplikacje, które są wydajne i łatwe w konserwacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 W tym artykule opisano podstawowe pojęcia transfer danych w usługach.  
  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 W tym artykule opisano, jakie dane kontraktów są oraz sposobu tworzenia i korzystania z nich.  
  
 [Serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Opisuje sposób wykonywania serializacji danych za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> klasy lub przedłużenia <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.  
  
 [Przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Opisuje, jak i dlaczego używać <xref:System.Xml.Serialization.XmlSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 [Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 W tym artykule opisano, jak kontrakty komunikatu umożliwia szczegółową kontrolę wiadomości SOAP.  
  
 [Używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Opisuje sposób korzystania z funkcji klasy wiadomości.  
  
 [Filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Opisuje filtrowania, które umożliwia przetwarzanie wstępne wiadomości na podstawie różnych kryteriów.  
  
 [Duże ilości danych i przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Opisuje sposób wysyłania dużych bloków danych, takich jak plik binarny.  
  
 [Zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 W tym artykule opisano elementy pod uwagę podczas programowania transfer i serializacja danych.  
  
 [Omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 W tym artykule opisano widok ogólnego projektu transferu danych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie koderów i serializatorów](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Przechowywanie wersji usługi](../../../../docs/framework/wcf/service-versioning.md)
