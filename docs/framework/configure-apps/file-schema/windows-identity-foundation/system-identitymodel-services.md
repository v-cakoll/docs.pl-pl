---
title: '&lt;system.identityModel.services&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a5f0b6b207fbd51504149fd5c245f41ef89f17f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemidentitymodelservicesgt"></a>&lt;system.identityModel.services&gt;
Sekcja konfiguracyjna do uwierzytelniania przy użyciu protokołu WS-Federation.  
  
 \<system.identityModel.services >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> moduły HTTP (SAM).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracji aplikacji, aby określić ustawienia SAM i WSFAM.  
  
> [!IMPORTANT]
>  Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie programu Menedżer autoryzacji oświadczeń (<xref:System.Security.Claims.ClaimsAuthorizationManager>) i zasad, która umożliwia podjęcie decyzji dotyczących autoryzacji są skonfigurowane za pomocą `<identityConfiguration>` element, który jest jawnie lub niejawnie wywoływany przez `<federationConfiguration>` element w tej sekcji. Aby uzyskać więcej informacji, zobacz **uwagi** w obszarze [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 `<system.identityModel.services>` Sekcji jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> klasy. Kolekcja podrzędnych `<federationConfiguration>` skonfigurowane w sekcji elementów jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> klasy.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML przedstawiono sposób dodawania `<system.identityModel.services>` sekcji w pliku konfiguracji. Najpierw należy dodać deklaracje sekcji zarówno `<system.identityModel.services>` sekcji i `<system.identityModel>` sekcje. (Po dodaniu `<system.identityModel.services>` sekcji, należy również dodać deklaracji `<system.identityModel>` sekcji, aby upewnić się, że domyślna `<identityConfiguration>` sekcji można tworzyć w czasie wykonywania, jeśli jest to konieczne.) Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"   
        issuer="http://localhost:15839/wsFederationSTS/Issue"   
        realm="http://localhost:50969/" reply="http://localhost:50969/"   
        requireHttps="false"   
        signOutReply="http://localhost:50969/SignedOutPage.html"   
        signOutQueryString="Param1=value2&Param2=value2"   
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
