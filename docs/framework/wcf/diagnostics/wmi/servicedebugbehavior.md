---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 76c4992c5364ed9800e58d120c099aceedb2799c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485684"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
