---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 330496d5f0f80affcb6bc44a1f66f4321a635f00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580593"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa BinaryMessageEncodingBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa BinaryMessageEncodingBindingElement ma następujące właściwości.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która określa rozmiar w bajtach buforu używany do kodowania.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Typ danych: XmlDictionaryReaderQuotas  
  
 Typ dostępu: tylko do odczytu  
  
 Przydziały czytników.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
