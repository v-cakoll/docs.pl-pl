---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: fdaf30e78b1a74a733753542acd6a41f15f176bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194831"
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
  
 Dostęp do typu: tylko do odczytu  
  
 Wersja powiadomienie ochrony prywatności.  
  
### <a name="url"></a>adres URL  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Adres URL, w której znajduje się powiadomienie dotyczące prywatności.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
