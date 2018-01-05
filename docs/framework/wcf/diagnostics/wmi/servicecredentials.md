---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Dostęp typu: tylko do odczytu  
  
 Certyfikat uwierzytelniania i dostarczania ustawień klienta dla tej usługi.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.  
  
### <a name="peer"></a>elementów równorzędnych  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Bieżące poświadczenia uwierzytelniania i dostarczania ustawienia używane przez punkty końcowego transportów elementów równorzędnych.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa bieżące ustawienia bezpiecznej konwersacji.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Certyfikat skojarzony z tą usługą.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia nazwy użytkownika i hasła dla tej usługi.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia uwierzytelniania systemu Windows dla tej usługi.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceCredentials>
