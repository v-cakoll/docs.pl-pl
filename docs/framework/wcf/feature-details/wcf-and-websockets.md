---
title: Program WCF i technologia WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: df4a251eb5a570c9fedf19d385a027e23481afed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594949"
---
# <a name="wcf-and-websockets"></a>Program WCF i technologia WebSockets
.NET Framework 4,5 wprowadza obsługę obiektów WebSockets w Windows Communication Foundation.  Obiekty WebSockets to wydajna technologia oparta na standardach, która umożliwia komunikację dwukierunkową za pośrednictwem standardowych portów HTTP 80 i 443. Użycie standardowych portów HTTP umożliwia komunikację między składnikami sieci Web za pośrednictwem pośredników.  Dodano dwa nowe powiązania standardowe do obsługi komunikacji przy użyciu protokołu WebSocket. <xref:System.ServiceModel.NetHttpBinding>i <xref:System.ServiceModel.NetHttpsBinding> . Ustawienia specyficzne dla obiektów WebSockets można skonfigurować w <xref:System.ServiceModel.Channels.HttpTransportBindingElement> programie, uzyskując dostęp do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> właściwości.
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie elementu NetHttpBinding](using-the-nethttpbinding.md)  
 W tym artykule omówiono <xref:System.ServiceModel.NetHttpBinding> i sposób konfigurowania tego programu.  
  
 [Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Opisuje sposób tworzenia usługi WCF, która komunikuje się za pośrednictwem obiektów WebSockets.  
  
## <a name="reference"></a>Dokumentacja  
  
## <a name="related-sections"></a>Sekcje pokrewne
