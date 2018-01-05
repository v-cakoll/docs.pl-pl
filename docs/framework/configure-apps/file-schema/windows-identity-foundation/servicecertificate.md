---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1373d1e95a0e569f5e5cf433d305d008b4daf838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt"></a>&lt;serviceCertificate&gt;
Umożliwia skonfigurowanie certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<serviceCertificate >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
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
|[\<certificateReference >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|Określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="example"></a>Przykład  
 Następujący kod XML pokazano sposób użycia \<serviceCertificate > elementu. Kod XML jest pobierana z `CustomToken` próbki.  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
