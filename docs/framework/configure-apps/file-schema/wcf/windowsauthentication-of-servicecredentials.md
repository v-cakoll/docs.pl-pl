---
title: <windowsAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ffddbae7effabcdafdc2638d588bbbf3e42d2c2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200392"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<windowsAuthentication > z \<serviceCredentials >
Określa ustawienia poświadczenia usługi Windows.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<windowsAuthentication>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`includeWindowsGroups`|Opcjonalny logiczny atrybut, który określa, czy system zawiera grupy Windows w kontekście zabezpieczeń. Wartość domyślna to `true`.<br /><br /> Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona wystąpił błąd rozszerzania grupy pełnej. Ustaw ten atrybut na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.|  
|`allowAnonymousLogons`|Opcjonalny logiczny atrybut, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania. Wartość domyślna to `false`.<br /><br /> Gdy `clientCredentialType` ma ustawioną wartość atrybutu powiązania `Windows`, system nie zezwala na dostęp anonimowy wywołań. Oznacza to, tym tylko domeny lub grupy roboczej uwierzytelniony obiekty wywołujące mogą uzyskać dostęp do systemu. To zachowanie można zastąpić za pomocą tego atrybutu.<br /><br /> Użyj tego ustawienia z najwyższą ostrożnością.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu, aby określić, czy chcesz zezwolić anonimowym użytkownikom Windows dostępu przez ustawienie `allowAnonymousLogons` atrybutu. Można również określić, czy do uwzględnienia informacji o grupie, do której należą użytkownicy w autoryzacji, ustawiając `includeWindowsGroups` atrybutu. Jeśli jest równa `true` (ustawienie domyślne), ta usługa może określić grupy Windows, do której należy dany klient.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
