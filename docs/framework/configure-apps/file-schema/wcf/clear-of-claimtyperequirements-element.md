---
title: <clear><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: e7e3bebd85decbaa4d216743f9bea9e135b87995
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926137"
---
# <a name="clear-of-claimtyperequirements-element"></a>\<Wyczyść > \<elementu claimTypeRequirements >
Określa, że wszystkie typy roszczeń mają być usunięte w poświadczeniu federacyjnym. Dzięki temu zbieranie danych jest puste.  
  
 \<system.ServiceModel>  
\<> powiązań  
\<wsFederatedBinding >  
\<> powiązania  
\<> zabezpieczeń  
\<message>  
\<claimTypeRequirements>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|Określa kolekcję wymaganych typów roszczeń. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń. Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
