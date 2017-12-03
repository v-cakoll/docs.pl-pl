---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
