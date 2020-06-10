---
title: Odnajdywanie w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 63c6589cb2ecff9f0a5e7c8bb61b454f6516c98c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600182"
---
# <a name="wcf-discovery"></a>Odnajdywanie w programie WCF
Windows Communication Foundation (WCF) zapewnia wsparcie umożliwiające odnajdywanie usług w środowisku uruchomieniowym w sposób współdziałający przy użyciu protokołu WS-Discovery. Usługi WCF mogą ogłaszać swoją dostępność do sieci przy użyciu komunikatu multiemisji lub serwera proxy odnajdywania. Aplikacje klienckie mogą przeszukiwać sieć lub serwer proxy odnajdywania, aby znaleźć usługi spełniające zestaw kryteriów. Tematy w tej sekcji zawierają omówienie i szczegółowo opisano model programowania tej funkcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie odnajdywania WCF](wcf-discovery-overview.md)  
 Zawiera omówienie obsługi protokołu WS-Discovery zapewnianej przez program WCF.  
  
 [Model obiektów odnajdywania WCF](wcf-discovery-object-model.md)  
 Opisuje klasy w modelu obiektów i rozszerzalność obsługi WS-Discovery.  
  
 [Instrukcje: programowe dodawanie możliwości odnajdywania do usługi i klienta WCF](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 Przedstawia sposób odnajdywania usługi Windows Communication Foundation (WCF).  
  
 [Implementowanie serwera proxy odnajdywania](implementing-a-discovery-proxy.md)  
 Opisuje kroki wymagane do zaimplementowania serwera proxy odnajdywania, usługi wykrywalnej, która rejestruje się za pomocą serwera proxy odnajdywania, i klienta korzystającego z serwera proxy odnajdywania w celu znalezienia usługi wykrywalnej.  
  
 [Przechowywanie wersji odnajdywania](discovery-versioning.md)  
 Zawiera krótkie omówienie implementacji prototypu niektórych nowych funkcji odnajdywania. Zawiera również omówienie sposobu wybierania wersji odnajdowania do użycia.  
  
 [Konfigurowanie odnajdywania w pliku konfiguracji](configuring-discovery-in-a-configuration-file.md)  
 Pokazuje, jak skonfigurować odnajdywanie w konfiguracji.  
  
 [Używanie kanału klienta odnajdywania](using-the-discovery-client-channel.md)  
 Pokazuje, jak używać kanału klienta odnajdywania podczas pisania aplikacji klienckiej programu WCF.
