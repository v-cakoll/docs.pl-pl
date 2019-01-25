---
title: Zapobieganie atakom polegającym na odtwarzaniu, gdy usługa WCF jest hostowana na farmie sieci Web
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: b0e52624ef4483672abd8cd0995dbc2e58f95ca1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684869"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Zapobieganie atakom polegającym na odtwarzaniu, gdy usługa WCF jest hostowana na farmie sieci Web
Jeśli korzystanie z zabezpieczeń komunikatów WCF zapobiega atakom metodą powtórzeń, tworząc JEDNORAZOWEGO poza komunikatu przychodzącego i sprawdzanie wewnętrzny `InMemoryNonceCache` czy wygenerowany identyfikator JEDNORAZOWY jest obecny. Jeśli tak jest, komunikat zostanie odrzucony jako powtarzania. Po usługi WCF jest hostowana na farmie sieci web ponieważ `InMemoryNonceCache` nie jest udostępniany między węzłami w farmie sieci web, usługa jest narażony na ataki.  Aby uniknąć tego scenariusza WCF 4.5 zapewnia punkt rozszerzalności, która pozwala na implementowanie własnych udostępnionej pamięci podręcznej JEDNORAZOWEGO przez wyprowadzanie klasy z klasy abstrakcyjnej <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>Implementacja NonceCache  
 Aby zaimplementować własną udostępnionej pamięci podręcznej (tymczasowo), należy wyprowadzić klasę z <xref:System.ServiceModel.Security.NonceCache> i zastąpić <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> i <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> metody. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> sprawdza, czy określony identyfikator JEDNORAZOWY istnieje w pamięci podręcznej. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> spróbuje dodać identyfikatora JEDNORAZOWEGO do pamięci podręcznej. Po zaimplementowaniu tej klasy można dołączyć go instancji, i przypisz go do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> wykrywania powtarzania dla klienta i <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> wykrywania powtarzania po stronie serwera. Nie ma żadnych poza wbudowanej obsługi konfiguracji dla tej funkcji.  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
