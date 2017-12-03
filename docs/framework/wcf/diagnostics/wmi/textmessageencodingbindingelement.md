---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 966f1ae06f5d7e0dacb8b7d450463c75f783ef1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement
TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa TextMessageEncodingBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa TextMessageEncodingBindingElement ma następujące właściwości:  
  
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
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
