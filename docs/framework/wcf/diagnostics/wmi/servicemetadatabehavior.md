---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976140"
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
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawia lokalizację, do której usługa przekierowuje żądania metadanych.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
