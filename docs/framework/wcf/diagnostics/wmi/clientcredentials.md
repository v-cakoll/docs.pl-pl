---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68a2fa36c8a4fa1fde3ca8d8aaf1898060ea972f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Dostęp typu: tylko do odczytu  
  
 Certyfikat X.509 klient używa do uwierzytelnienia w usłudze.  
  
### <a name="httpdigest"></a>HttpDigest  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Bieżące poświadczenie Http Digest.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Adres punktu końcowego i powiązanie używane do kontaktu z usługą tokenu zabezpieczeń lokalnych.  
  
### <a name="peer"></a>elementów równorzędnych  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Poświadczenia używane przez węzeł elementu równorzędnego do samodzielnego uwierzytelnienia w innych węzłach w sieci.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Certyfikat X.509 usługi.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy poświadczenie obsługuje interaktywną negocjację.  
  
### <a name="username"></a>UserName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.  
  
### <a name="windows"></a>Windows  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Poświadczenia systemu windows używa klienta do samodzielnego uwierzytelnienia usługi.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ClientCredentials>
