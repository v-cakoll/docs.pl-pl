---
title: '&lt;system.identityModel&gt;'
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6faeadc9fcdffc8c8aa14fdcc744896b45a941f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemidentitymodelgt"></a>&lt;system.identityModel&gt;
Zapewnia konfigurację Włączanie opcji Windows Identity Foundation (WIF) w aplikacji.  
  
 \<system.identityModel>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości poziomu usług.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<configuration>`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Dodaj `<system.identityModel>` sekcji pliku konfiguracji, aby skonfigurować usługę lub aplikację do używania systemu Windows Identity Foundation (WIF). `<system.identityModel>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania `<system.identityModel>` sekcji w pliku konfiguracji. Najpierw należy dodać konfiguracji deklaracji sekcji i przestrzeni nazw w obszarze `<configSections>` elementu. Następnie można dodać `<system.IdentityModel>` elementu do pliku konfiguracji, aby określić co najmniej jednej konfiguracji tożsamości.  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
