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
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136971"
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
|`dclDemand`|Wszystkie podmioty wywołujące wyżej w stosie wywołań są wymagane do udzielono uprawnienia określone przez bieżący obiekt uprawnień.|  
|`dclAssert`|Kod wywołujący może uzyskać dostępu do zasobu, identyfikowane przez bieżący obiekt uprawnienia, nawet wtedy, gdy wyżej w stosie wywołań nie przyznano uprawnień dostępu do zasobu|  
|`dclDeny`|Możliwość dostępu do zasobu, określony przez bieżący obiekt uprawnień nie jest możliwy obiektów wywołujących, nawet wtedy, gdy przyznano im uprawnienia dostępu do niego.|  
|`dclPermitOnly`|Tylko zasoby, które zostały określone przez ten obiekt uprawnień są dostępne, nawet jeśli kod ma uprawnienia dostępu do innych zasobów.|  
|`dclLinktimeCheck`|Do bezpośredniego wywołującego jest wymagana do przyznano określone uprawnienie dla danego okresu czasu.|  
|`dclInheritanceCheck`|Klasa pochodna dziedziczy innej klasy lub zastępowania metody jest wymagany do przyznano określone uprawnienie.|  
|`dclRequestMinimum`|Obiekt wywołujący może żądać minimalne uprawnienia wymagane do kod wymagany do uruchomienia. Tej akcji należy używać tylko w ramach zakresu zestawu.|  
|`dclRequestOptional`|Obiekt wywołujący może żądać uzyskać dodatkowe uprawnienia, które są opcjonalne (nie wymaga do uruchomienia). To żądanie niejawnie odmawia innych uprawnień nie jest wymagane. Tej akcji należy używać tylko w ramach zakresu zestawu.|  
|`dclRequestRefuse`|Żądanie obiektu wywołującego uprawnienia, które mogą być używane nie zostaną przyznane. Tej akcji należy używać tylko w ramach zakresu zestawu.|  
|`dclPrejitGrant`|Zastrzeżone.|  
|`dclPrejitDenied`|Zastrzeżone.|  
|`dclNonCasDemand`|Zastrzeżone.|  
|`dclNonCasLinkDemand`|Bezpośredniego obiektu wywołującego jest wymagana do przyznano określone uprawnienie.|  
|`dclNonCasInheritance`|Zastrzeżone.|  
|`dclLinkDemandChoice`|Zastrzeżone.|  
|`dclInheritanceDemandChoice`|Zastrzeżone.|  
|`dclDemandChoice`|Zastrzeżone.|  
|`dclMaximumValue`|Zastrzeżone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
