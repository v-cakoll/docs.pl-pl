---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 410a133ae3041db00ecb7a17677afe6538ef1f4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632741"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ClientCredentials nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ClientCredentials ma następujące właściwości:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Certyfikat X.509, klient używa do uwierzytelnienia w usłudze.  
  
### <a name="httpdigest"></a>HttpDigest  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Bieżące poświadczenie Http Digest.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Adres punktu końcowego i powiązania używanego do kontaktowania się z usługi tokenu zabezpieczeń lokalnych.  
  
### <a name="peer"></a>Elementu równorzędnego  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Poświadczenia używane przez węzeł równorzędny uwierzytelnienie na innych węzłach w sieci.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Certyfikat X.509 dla usługi.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca, czy poświadczenia obsługuje interakcyjne negocjacji.  
  
### <a name="username"></a>UserName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.  
  
### <a name="windows"></a>Windows  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Windows poświadczeń używa klienta do samodzielnego uwierzytelnienia usługi.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Description.ClientCredentials>
