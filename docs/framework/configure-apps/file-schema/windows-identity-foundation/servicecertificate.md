---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942413"
---
# <a name="servicecertificate"></a>\<> serviceCertificate
Konfiguruje certyfikat X. 509, który jest używany do szyfrowania i odszyfrowywania tokenów.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<> serviceCertificate  
  
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
|[\<certificateReference >](certificatereference.md)|Określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia użycie \<elementu serviceCertificate >. Kod XML jest pobierany z `CustomToken` przykładu.  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
