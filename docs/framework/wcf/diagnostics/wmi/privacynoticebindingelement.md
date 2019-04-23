---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: 04c65d0aa589d99766b4ffc8f1550036d2880718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976381"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa PrivacyNoticeBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa PrivacyNoticeBindingElement ma następujące właściwości:  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Wersja powiadomienie ochrony prywatności.  
  
### <a name="url"></a>adres URL  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Adres URL, w której znajduje się powiadomienie dotyczące prywatności.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
