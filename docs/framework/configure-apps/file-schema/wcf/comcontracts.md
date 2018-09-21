---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 297a28181de8ce6ed658afad950f25cced9f9cb7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540807"
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` Sekcja konfiguracji zawiera elementy, które pozwalają określić różne właściwości kontraktu usługi integracji COM +.  
  
## <a name="specifying-namespace-and-contract"></a>Określanie Namespace i umowy  
 Kontrakty usług integracji modelu COM + są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw i Nazwa kontraktu jest tworzony na podstawie obsługi interfejsu COM. Można jednak określić alternatywne przy użyciu `comContracts` sekcji w pliku konfiguracji.  
  
 Na przykład można użyć następującej konfiguracji do określenia nazwy przestrzeni nazw i kontrakt kontraktu usługi, a także opcję, aby wymusić użycie na powiązaniach sesyjnych.  
  
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
  
 Ta sekcja jest pusta, inicjowanie usługi zastosowanie domyślnej nazwy przestrzeni nazw i umowy z pomocniczych identyfikatora interfejsu COM  
  
 Ponadto można użyć [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementu, aby określić metody COM +, które są udostępniane, gdy interfejs składnika COM + jest widoczny jako usługi sieci Web. Można również użyć [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) Aby określić typy stałe używane w integracji. Na koniec można użyć [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element, aby uwzględnić użytkowników zdefiniowanych typów (UDT), które mają być uwzględniane w kontrakcie usługi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Współdziałanie z aplikacjami COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Instrukcje: konfigurowanie ustawień usługi COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
