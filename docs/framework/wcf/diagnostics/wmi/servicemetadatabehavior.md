---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188836"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementu ServiceMetadataBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementu ServiceMetadataBehavior ma następujące właściwości:  
  
### <a name="externalmetadatalocation"></a>externalMetadataLocation  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawia lokalizację, do której usługa przekierowuje żądania metadanych.  
  
### <a name="httpgetenabled"></a>httpGetEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.  
  
### <a name="httpgeturl"></a>httpGetUrl  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.  
  
### <a name="httpsgetenabled"></a>httpsGetEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.  
  
### <a name="httpsgeturl"></a>httpsGetUrl  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
