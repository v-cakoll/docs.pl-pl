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
# <a name="data-transfer-and-serialization"></a>Transfer i serializacja danych
W połączonym systemie usługi i klienci zależą od wymiany danych w celu wykonania dowolnego zadania. Jako deweloper usługi lub klienta należy również zrozumieć, w jaki sposób Windows Communication Foundation (WCF) obsługuje dane i serializacji danych w celu tworzenia aplikacji, które są wydajne i łatwe w obsłudze.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie transferu danych w kontraktach usług](specifying-data-transfer-in-service-contracts.md)  
 Zawiera opis podstawowych pojęć związanych z transferem danych w usługach.  
  
 [Używanie kontraktów danych](using-data-contracts.md)  
 Zawiera opis umów dotyczących danych i sposobu ich tworzenia i używania.  
  
 [Serializator kontraktów danych](data-contract-serializer.md)  
 Opisuje, w jaki sposób wykonać serializacji danych z <xref:System.Runtime.Serialization.DataContractSerializer> klasą lub dowolnym rozszerzeniem <xref:System.Runtime.Serialization.XmlObjectSerializer> klasy.  
  
 [Używanie klasy XmlSerializer](using-the-xmlserializer-class.md)  
 Opisuje, jak i dlaczego należy używać <xref:System.Xml.Serialization.XmlSerializer> klasy, alternatywy dla <xref:System.Runtime.Serialization.DataContractSerializer> klasy.  
  
 [Używanie kontraktów komunikatu](using-message-contracts.md)  
 Opisuje sposób, w jaki kontrakty komunikatów umożliwiają kontrolę nad komunikatami protokołu SOAP.  
  
 [Używanie klasy Message](using-the-message-class.md)  
 Opisuje sposób korzystania z funkcji klasy komunikatów.  
  
 [Filtrowanie](filtering.md)  
 Opisuje filtrowanie, które umożliwia wstępne przetwarzanie wiadomości na podstawie różnych kryteriów.  
  
 [Duże ilości danych i przesyłanie strumieniowe](large-data-and-streaming.md)  
 Opisuje sposób wysyłania dużego bloku danych, takiego jak plik binarny.  
  
 [Zagadnienia związane z zabezpieczeniami danych](security-considerations-for-data.md)  
 Opisuje elementy, które mają być świadome podczas programowania transferu i serializacji danych.  
  
 [Omówienie architektury transferu danych](data-transfer-architectural-overview.md)  
 Opisuje widok ogólnego projektu transferu danych w programie WCF.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie koderów i serializatorów](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Zobacz też

- [Najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../best-practices-data-contract-versioning.md)
- [Przechowywanie wersji usługi](../service-versioning.md)
