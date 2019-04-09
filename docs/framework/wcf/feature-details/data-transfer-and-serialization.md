---
title: Transfer i serializacja danych
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 1eefd82a149d0bc215ca441e92c7d737a744b1e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088408"
---
# <a name="data-transfer-and-serialization"></a>Transfer i serializacja danych
W systemie połączonych usług i klientów są zależne od wymiany danych, aby wykonać dowolne zadanie. Jako deweloper usługi lub klienta również należy zrozumieć, jak Windows Communication Foundation (WCF) obsługuje dane i serializacja danych w celu tworzenia aplikacji, które są wydajne i łatwa w obsłudze.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 W tym artykule opisano podstawowe pojęcia transferu danych w usługach.  
  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 W tym artykule opisano, jakie dane zamówień są i jak tworzyć i używać ich.  
  
 [Serializator kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 W tym artykule opisano sposób wykonywania serializacji danych za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> klasy lub dowolnego rozszerzenia <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.  
  
 [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Opisuje, jak i dlaczego warto używać <xref:System.Xml.Serialization.XmlSerializer> klasy zamiast <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 [Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 W tym artykule opisano, jak kontrakty komunikatów umożliwia szczegółową kontrolę komunikaty protokołu SOAP.  
  
 [Używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 W tym artykule opisano, jak korzystać z funkcji klasy wiadomości.  
  
 [Filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md)  
 W tym artykule opisano, filtrowania, które umożliwia wstępne przetwarzanie komunikatów, na podstawie różnych kryteriów.  
  
 [Duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 W tym artykule opisano sposób wysyłania dużych bloków danych, takich jak plik binarny.  
  
 [Zagadnienia związane z zabezpieczeniami danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 W tym artykule opisano elementy, których trzeba pamiętać podczas programowania transfer i serializacja danych.  
  
 [Omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Opisuje widok ogólnego projektu transferu danych programu WCF.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie koderów i serializatorów](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Przechowywanie wersji usługi](../../../../docs/framework/wcf/service-versioning.md)
