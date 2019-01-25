---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 188a766807cd779ac51df390b1332641584dbb06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662715"
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement
TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Typ dostępu: tylko do odczytu  
  
 Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Typ danych: XmlDictionaryReaderQuotas  
  
 Typ dostępu: tylko do odczytu  
  
 Przydziały czytników.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
