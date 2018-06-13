---
title: CorDeclSecurity — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7512795e678f66c97185a499e602e99f51188117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443027"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity — Wyliczenie
Określa akcje zabezpieczeń, które mogą być wykonywane przy użyciu zabezpieczeń deklaratywnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dclActionMask`|Zastrzeżone.|  
|`dclActionNil`|Zastrzeżone.|  
|`dclRequest`|Zastrzeżone.|  
|`dclDemand`|Wszystkie obiekty wywołujące wyżej w stosie wywołań są wymagane do otrzymali uprawnienia określone przez bieżący obiekt uprawnień.|  
|`dclAssert`|Kod wywołujący ma dostęp do zasobu identyfikowana na podstawie bieżącego obiektu uprawnienia, nawet jeśli wyżej w stosie wywołań nie przyznano uprawnień dostępu do zasobu|  
|`dclDeny`|Możliwość dostępu do zasobu określonego przez bieżący obiekt uprawnienia Odmowa dla kodu wywołującego, nawet wtedy, gdy przyznano im uprawnienia dostępu do niego.|  
|`dclPermitOnly`|Tylko zasoby określone przez ten obiekt uprawnienia są dostępne, nawet jeśli kod ma uprawnienia dostępu do innych zasobów.|  
|`dclLinktimeCheck`|Bezpośredniego obiektu wywołującego jest wymagany do przyznano określonego uprawnienia w danym okresie czasu.|  
|`dclInheritanceCheck`|Klasy pochodnej dziedziczenia innej klasy lub przesłaniania metody jest wymagany do przyznano określonego uprawnienia.|  
|`dclRequestMinimum`|Obiekt wywołujący może wysłać żądanie minimalne uprawnienia wymagane przez kod wymagany do uruchomienia. Ta akcja można używać tylko w zakresie zestawu.|  
|`dclRequestOptional`|Obiekt wywołujący może wysłać żądanie uzyskania dodatkowych uprawnień, które są opcjonalne (nie trzeba uruchamiać). To żądanie odmawia niejawnie innych uprawnień nie pobrany na żądanie. Ta akcja można używać tylko w zakresie zestawu.|  
|`dclRequestRefuse`|Nie otrzyma żądanie wywołującego uprawnienia, które mogą być używane. Ta akcja można używać tylko w zakresie zestawu.|  
|`dclPrejitGrant`|Zastrzeżone.|  
|`dclPrejitDenied`|Zastrzeżone.|  
|`dclNonCasDemand`|Zastrzeżone.|  
|`dclNonCasLinkDemand`|Bezpośredniego obiektu wywołującego jest wymagany do przyznano określonego uprawnienia.|  
|`dclNonCasInheritance`|Zastrzeżone.|  
|`dclLinkDemandChoice`|Zastrzeżone.|  
|`dclInheritanceDemandChoice`|Zastrzeżone.|  
|`dclDemandChoice`|Zastrzeżone.|  
|`dclMaximumValue`|Zastrzeżone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
