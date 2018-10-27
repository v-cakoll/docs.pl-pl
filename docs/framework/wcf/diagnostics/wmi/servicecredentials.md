---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 26bd0c95f930bf7859ae6409d797afbb596844fa
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180670"
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
  
 Dostęp do typu: tylko do odczytu  
  
 Certyfikat uwierzytelniania i inicjowania obsługi ustawień klienta dla tej usługi.  
  
### <a name="issuedtokenauthentication"></a>issuedTokenAuthentication  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.  
  
### <a name="peer"></a>Elementu równorzędnego  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Bieżący poświadczeń uwierzytelniania i inicjowania obsługi ustawienia używane przez punkty końcowe transport elementu równorzędnego.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa bieżące ustawienia bezpiecznej konwersacji.  
  
### <a name="servicecertificate"></a>serviceCertificate  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Certyfikat skojarzony z tą usługą.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawienia nazwy użytkownika i hasła dla tej usługi.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawienia uwierzytelniania Windows dla tej usługi.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceCredentials>
