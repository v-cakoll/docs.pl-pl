---
title: "Protokół PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 805f6f6ed7990b42065dfe7985a5d81844961897
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="peer-name-resolution-protocol"></a>Protokół PNRP
W środowiskach peer-to-peer elementów równorzędnych użyć systemy rozpoznawania nazw określonych w ustalaniu każdej lokalizacji sieciowych (adresów, protokołów i portów) na podstawie nazw lub identyfikatorów innego typu. W przeszłości rozpoznawania nazw równorzędnych o zostały skomplikowanym łączności z założenia przejściowy, a także innych braków w ramach systemu nazw domen (DNS).  
  
 Microsoft® Windows® sieci Peer-to-Peer platformy rozwiązuje ten problem z rozpoznawania protokołu PNRP (Peer Name), bezpieczna, skalowalna i dynamicznych rejestracji i protokołu rozpoznawania nazw zaprojektowane dla systemu Windows XP, a następnie uaktualnionego na Vista™ systemu Windows. Usługa PNRP działa bardzo różniący się od tradycyjnych protokołów rozpoznawania nazw, otwieranie ekscytujące nowe możliwości dla deweloperów aplikacji.  
  
 Usłudze PNRP nazwy elementów równorzędnych może odnosić się do komputera, lub poszczególnych aplikacji lub usług na komputerze. Rozpoznawanie nazw elementów równorzędnych obejmuje adres, port i prawdopodobnie Ładunek rozszerzony. Ten system zalety odporność na uszkodzenia, nie wąskich gardeł i nazwy rozwiązania, które nigdy nie zwróci stare adresy; wprowadzenie protokołu idealnym rozwiązaniem służącym do lokalizowania użytkowników mobilnych.  
  
 Pod względem zabezpieczeń, nazwy elementów równorzędnych może być publikowane jako zabezpieczonych (chronionej) lub niezabezpieczona (bez ochrony). Usługa PNRP wykorzystuje kryptografię klucza publicznego do ochrony nazwy bezpiecznego elementów równorzędnych przed fałszowaniem; zarówno komputery i usługi mogą mieć nazwę w usłudze PNRP.  
  
-   Protokołu rozpoznawania nazw równorzędnych przedstawiono następujące właściwości:  
  
-   Rozproszone i prawie całkowicie niekorzystającą. Serwery są tylko wymagane dla bootstrapping procesu.  
  
-   Zabezpiecz nazwa publikacji bez udziału osób trzecich. W przeciwieństwie do publikacji nazwy DNS publikowanie nazw PNRP jest natychmiastowe i bez ponoszenia kosztów finansowych.  
  
-   Aktualizacje PNRP w czasie rzeczywistym, co uniemożliwia rozpoznawanie stare adresy.  
  
-   Rozpoznawanie nazw za pomocą PNRP wykracza poza komputerów zezwalając również rozpoznawania nazw dla usług.  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Namespace System.Net.PeerToPeer  
  
-   Funkcje PNRP jest definiowana za pomocą <xref:System.Net.PeerToPeer> przestrzeni nazw w .NET Framework w wersji 3.5. Zapewnia zestaw typów, które mogą służyć do rejestrowania i rozpoznawania nazw równorzędnych o dostępności usługi PNRP.  
  
-  
  
-   (PNRP i mechanizmy rozpoznawania elementów równorzędnych niestandardowe można tworzyć i wystąpień typów przy użyciu dostępnych w <xref:System.ServiceModel.PeerResolvers> przestrzeni nazw.)  
  
-  
  
-   Podstawowe typy używane do rejestrowania i rozpoznawania nazw w usłudze PNRP dostępne są następujące:  
  
-  
  
-   <xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępne chmurze usługi PNRP, w tym zakresie.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Określa nazwę elementu równorzędnego, który może służyć do rejestrowania i następnie rozpoznawania elementu równorzędnego w chmurze.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: Określa rekord w chmurze usługi PNRP, który zawiera informacje o rejestracji dla elementu równorzędnego, w tym punktów końcowych sieci, w których można się skontaktować elementu równorzędnego.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje proces rejestracji w celu nazwa elementu równorzędnego, łącznie z metody służące do uruchamiania i zatrzymywania rejestracji nazw elementów równorzędnych.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazw równorzędnych do jego punktów końcowych sieci, w tym synchroniczne i asynchroniczne metod rozpoznawania.  
  
-  
  
-  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [Przykłady programowania w języku sieci](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Technologia PeerToPeer próbki](http://go.microsoft.com/fwlink/?LinkID=179571)
