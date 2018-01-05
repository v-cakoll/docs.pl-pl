---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cc36d7daed1a2cfaf050cbfe9661951117ff66d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa MtomMessageEncodingBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa MtomMessageEncodingBindingElement ma następujące właściwości:  
  
### <a name="encoding"></a>Kodowanie  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Zestaw znaków kodowania używanego w celu emisji komunikatów w powiązaniu.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Typ danych: XmlDictionaryReaderQuotas  
  
 Dostęp typu: tylko do odczytu  
  
 Przydziały czytników.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
