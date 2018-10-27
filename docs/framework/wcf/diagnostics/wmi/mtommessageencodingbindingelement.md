---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 49a640a666131491366646d6d486d25a515e35bf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185709"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Dostęp do typu: tylko do odczytu  
  
 Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.  
  
### <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.  
  
### <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.  
  
### <a name="readerquotas"></a>readerQuotas  
 Typ danych: XmlDictionaryReaderQuotas  
  
 Dostęp do typu: tylko do odczytu  
  
 Przydziały czytników.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
