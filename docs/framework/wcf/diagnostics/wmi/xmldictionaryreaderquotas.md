---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980534"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna dozwolona długość tablicy.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna dozwolona liczba bajtów zwróconych do każdego odczytu.  
  
### <a name="maxdepth"></a>MaxDepth  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna głębokość zagnieżdżonego węzła dla każdego do odczytu.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna dozwolona liczba znaków w nazwie tabeli.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna dozwolona liczba znaków w elemencie zawartości XML.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
