---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251793"
---
# <a name="systemidentitymodel"></a>\<system.identityModel>
Zapewnia konfigurację umożliwiającą włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp; **\<> System. identityModel**  
  
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
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<configuration>`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 `<system.identityModel>` Dodaj sekcję do pliku konfiguracji, aby skonfigurować usługę lub aplikację do korzystania z programu Windows Identity Foundation (WIF). Element jest reprezentowany <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> przez klasę. `<system.identityModel>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać `<system.identityModel>` sekcję do pliku konfiguracji. Najpierw należy dodać sekcję konfiguracyjną i deklarację przestrzeni nazw w `<configSections>` ramach elementu. Następnie można dodać `<system.IdentityModel>` element do pliku konfiguracji, aby określić co najmniej jedną konfigurację tożsamości.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
