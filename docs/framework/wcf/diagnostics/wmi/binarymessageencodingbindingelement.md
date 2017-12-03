---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementu BinaryMessageEncodingBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementu BinaryMessageEncodingBindingElement ma następujące właściwości.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która określa rozmiar w bajtach buforu używany do kodowania.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Typ danych: XmlDictionaryReaderQuotas  
  
 Dostęp typu: tylko do odczytu  
  
 Przydziały czytników.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
