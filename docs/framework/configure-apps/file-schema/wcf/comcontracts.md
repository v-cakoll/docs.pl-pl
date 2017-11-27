---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 168bd57652aca5f3c1b61c90abea5288bd1a6719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` Sekcja konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji COM +.  
  
## <a name="specifying-namespace-and-contract"></a>Określanie Namespace i kontraktu  
 Kontrakty usług integracji COM + są obecnie ograniczone do przestrzeni nazw "http://tempuri.org", a Nazwa kontraktu pochodzi od obsługi interfejsu COM. Można jednak określić alternatywne przy użyciu `comContracts` sekcji w pliku konfiguracji.  
  
 Na przykład można użyć następującej konfiguracji do określenia nazwy przestrzeni nazw i kontraktu kontraktu usługi, a także opcję, aby wymusić użycie na powiązaniach sesyjnych.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 Podczas inicjowania usługi określonych przestrzeni nazw i nazwy kontraktów są stosowane do opisów wygenerowanego usługi.  
  
 Ta sekcja jest pusta, inicjowanie usługi zastosowanie domyślną nazwę przestrzeni nazw i kontraktu pobranych z identyfikatorem obsługi interfejsu COM  
  
 Ponadto można użyć [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element, aby określić metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web. Można również użyć [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) do określenia możliwy do utrwalenia typów używanych w integracji. Ponadto można użyć [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element, aby dołączyć użytkownika zdefiniowanych typów (UDT), które mają być uwzględniane w kontrakcie usługi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Współdziałanie z aplikacjami COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Porady: Konfigurowanie ustawień usług COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
