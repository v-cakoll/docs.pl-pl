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
ms.openlocfilehash: ffbc9a10ff48b3dfd59b95c0f6b9ecab80b6a49c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007887"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity — Wyliczenie
Określa akcje zabezpieczeń, które mogą być wykonywane przy użyciu zabezpieczeń deklaratywnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`dclActionMask`|Zarezerwowany.|  
|`dclActionNil`|Zarezerwowany.|  
|`dclRequest`|Zarezerwowany.|  
|`dclDemand`|Wszystkie obiekty wywołujące wyższe w stosie wywołań muszą mieć przyznane uprawnienia określone przez bieżący obiekt uprawnień.|  
|`dclAssert`|Kod wywołujący może uzyskać dostęp do zasobu identyfikowanego przez bieżący obiekt uprawnień, nawet jeśli obiekty wywołujące wyższe w stosie nie uzyskały uprawnień dostępu do zasobu|  
|`dclDeny`|Możliwość dostępu do zasobu określonego przez bieżący obiekt uprawnień jest odrzucana dla wywołujących, nawet jeśli udzielono uprawnień dostępu do niej.|  
|`dclPermitOnly`|Dostęp do zasobów określonych przez ten obiekt uprawnień można uzyskać nawet wtedy, gdy do kodu udzielono uprawnień dostępu do innych zasobów.|  
|`dclLinktimeCheck`|Bezpośredni obiekt wywołujący musi mieć przyznane określone uprawnienie w danym okresie czasu.|  
|`dclInheritanceCheck`|Klasa pochodna dziedziczenia innej klasy lub przesłaniania metody jest wymagana do przyznania określonego uprawnienia.|  
|`dclRequestMinimum`|Obiekt wywołujący może żądać minimalnych uprawnień wymaganych do uruchomienia kodu. Tej akcji można używać tylko w zakresie zestawu.|  
|`dclRequestOptional`|Obiekt wywołujący może żądać dodatkowych uprawnień, które są opcjonalne (niewymagane do uruchomienia). To żądanie niejawnie odrzuca wszystkie inne uprawnienia, które nie zostały zażądane. Tej akcji można używać tylko w zakresie zestawu.|  
|`dclRequestRefuse`|Żądanie obiektu wywołującego dla uprawnień, które mogą być nieużywane, nie zostanie przyznane. Tej akcji można używać tylko w zakresie zestawu.|  
|`dclPrejitGrant`|Zarezerwowany.|  
|`dclPrejitDenied`|Zarezerwowany.|  
|`dclNonCasDemand`|Zarezerwowany.|  
|`dclNonCasLinkDemand`|Bezpośredni obiekt wywołujący musi mieć przyznane określone uprawnienie.|  
|`dclNonCasInheritance`|Zarezerwowany.|  
|`dclLinkDemandChoice`|Zarezerwowany.|  
|`dclInheritanceDemandChoice`|Zarezerwowany.|  
|`dclDemandChoice`|Zarezerwowany.|  
|`dclMaximumValue`|Zarezerwowany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
