---
title: Transfer i serializacja danych
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 53c1421bf14c598611e116c61353c4ecd465f1aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489209"
---
# <a name="data-transfer-and-serialization"></a>Transfer i serializacja danych
W systemie połączonych usług i klientów są zależne od wymiany danych, wykonywać wszystkie zadania. Jako deweloper usługi lub klienta należy również poznać, jak Windows Communication Foundation (WCF) obsługuje dane i serializacja danych w celu tworzenia aplikacji, które są wydajne i łatwe w konserwacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 W tym artykule opisano podstawowe pojęcia transfer danych w usługach.  
  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 W tym artykule opisano, jakie dane kontraktów są oraz sposobu tworzenia i korzystania z nich.  
  
 [Serializator kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Opisuje sposób wykonywania serializacji danych za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> klasy lub przedłużenia <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.  
  
 [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Opisuje, jak i dlaczego używać <xref:System.Xml.Serialization.XmlSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 [Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 W tym artykule opisano, jak kontrakty komunikatu umożliwia szczegółową kontrolę wiadomości SOAP.  
  
 [Używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Opisuje sposób korzystania z funkcji klasy wiadomości.  
  
 [Filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Opisuje filtrowania, które umożliwia przetwarzanie wstępne wiadomości na podstawie różnych kryteriów.  
  
 [Duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Opisuje sposób wysyłania dużych bloków danych, takich jak plik binarny.  
  
 [Zagadnienia związane z zabezpieczeniami danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 W tym artykule opisano elementy pod uwagę podczas programowania transfer i serializacja danych.  
  
 [Omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 W tym artykule opisano widok ogólnego projektu transfer danych w programie WCF.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie koderów i serializatorów](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Przechowywanie wersji usługi](../../../../docs/framework/wcf/service-versioning.md)
