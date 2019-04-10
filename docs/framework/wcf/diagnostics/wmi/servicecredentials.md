---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230931"
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceCredentials nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceCredentials ma następujące właściwości:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Certyfikat uwierzytelniania i inicjowania obsługi ustawień klienta dla tej usługi.  
  
### <a name="issuedtokenauthentication"></a>issuedTokenAuthentication  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.  
  
### <a name="peer"></a>Elementu równorzędnego  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Bieżący poświadczeń uwierzytelniania i inicjowania obsługi ustawienia używane przez punkty końcowe transport elementu równorzędnego.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Określa bieżące ustawienia bezpiecznej konwersacji.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Certyfikat skojarzony z tą usługą.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawienia nazwy użytkownika i hasła dla tej usługi.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawienia uwierzytelniania Windows dla tej usługi.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceCredentials>
