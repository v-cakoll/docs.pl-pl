---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69919477"
---
# \<comContracts>
`comContracts`Sekcja konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji modelu com+.  
  
## <a name="specifying-namespace-and-contract"></a>Określanie przestrzeni nazw i kontraktu  
 Kontrakty usługi integracji modelu COM+ są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw, a nazwa kontraktu pochodzi od pomocniczego interfejsu com. Można jednak określić alternatywy przy użyciu `comContracts` sekcji w pliku konfiguracji.  
  
 Można na przykład użyć poniższej konfiguracji, aby określić przestrzeń nazw i nazwę kontraktu dla kontraktu usługi, a także opcję wymuszać użycie na powiązaniach sesji.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 Po zainicjowaniu usługi określone nazwy obszarów nazw i kontraktów są stosowane do opisów wygenerowanych usług.  
  
 Gdy ta sekcja jest pusta, Inicjalizacja usługi stosuje domyślną przestrzeń nazw i nazwę kontraktu pobraną z pomocniczego identyfikatora interfejsu COM.  
  
 Ponadto można użyć [\<exposedMethod>](exposedmethod.md) elementu, aby określić metody modelu COM+, które są dostępne, gdy interfejs składnika modelu com+ jest uwidoczniony jako usługa sieci Web. Można również użyć, [\<persistableTypes>](persistabletypes.md) Aby określić typy utrwalane używane w integracji. Na koniec można użyć elementu, [\<userDefinedType>](userdefinedtype.md) Aby uwzględnić typy zdefiniowane przez użytkownika (UDT), które mają zostać uwzględnione w kontrakcie usługi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [Integrowanie z aplikacjami COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Instrukcje: konfigurowanie ustawień usługi COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
