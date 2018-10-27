---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 68b2350f257bc95d8e17f4b9049d67c7f67becae
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452865"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceDebugBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceDebugBehavior ma następujące właściwości:  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>Parametr IncludeExceptionDetailInFaults  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
