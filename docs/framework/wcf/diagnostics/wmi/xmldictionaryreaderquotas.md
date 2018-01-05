---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a3afb9b8cfede60c773d146f4d1728d7fe02b75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Składnia  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa obiektu XmlDictionaryReaderQuotas nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa obiektu XmlDictionaryReaderQuotas ma następujące właściwości:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna dozwolona długość tablicy.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna dozwolona liczba bajtów zwracana przy każdym odczycie.  
  
### <a name="maxdepth"></a>MaxDepth  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna głębokość zagnieżdżenia węzłów przy każdym odczycie.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna dozwolona liczba znaków w nazwie tabeli.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba znaków dozwolona w zawartości elementu XML.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
