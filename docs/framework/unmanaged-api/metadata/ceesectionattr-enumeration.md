---
title: CeeSectionAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 97b28c961f43388679615ac0d5b19c4c69df1e3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444247"
---
# <a name="ceesectionattr-enumeration"></a>CeeSectionAttr — Wyliczenie
Zawiera wartości określające atrybuty sekcji, która ma być używana przez interfejs [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`sdNone`|Sekcja nie ma żadnych atrybutów.|  
|`sdReadOnly`|Sekcja zawiera zainicjowane dane, które mogą być tylko do odczytu, a nie zaktualizowane.|  
|`sdReadWrite`|Sekcja zawiera zainicjowane dane, które można odczytać lub zaktualizować.|  
|`sdExecute`|Sekcja zawiera kod wykonywalny, który może być odczytywany i wykonywany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
