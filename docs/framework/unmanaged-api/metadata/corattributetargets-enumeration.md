---
title: CorAttributeTargets — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: f1836f26af99f91ab1765107573f6b067edd5e95
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007926"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets — Wyliczenie
Określa elementy aplikacji, na których jest prawidłowy, aby zastosować atrybut.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`catAssembly`|Atrybut może zostać zastosowany do zestawu.|  
|`catModule`|Atrybut można zastosować do przenośnego modułu pliku wykonywalnego (. dll lub. exe).|  
|`catClass`|Atrybut może być stosowany do klasy.|  
|`catStruct`|Atrybut może być stosowany do struktury; oznacza to, że typ wartości.|  
|`catEnum`|Atrybut może być stosowany do wyliczenia.|  
|`catConstructor`|Atrybut może być stosowany do konstruktora.|  
|`catMethod`|Atrybut można zastosować do metody.|  
|`catProperty`|Atrybut może być stosowany do właściwości.|  
|`catField`|Atrybut może być stosowany do pola.|  
|`catEvent`|Atrybut może być stosowany do zdarzenia.|  
|`catInterface`|Atrybut może być stosowany do interfejsu.|  
|`catParameter`|Atrybut może być stosowany do parametru.|  
|`catDelegate`|Atrybut można zastosować do obiektu delegowanego.|  
|`catGenericParameter`|Atrybut może być stosowany do parametru generycznego.|  
|`catAll`|Atrybut można zastosować do dowolnego elementu aplikacji.|  
|`catClassMembers`|Atrybut można zastosować do składowej klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `CorAttributeTargets`Wartości wyliczenia można łączyć z wartością bitową lub operacją w celu uzyskania preferowanej kombinacji.  
  
 `CorAttributeTargets`Równolegle zarządzanym <xref:System.AttributeTargets?displayProperty=nameWithType> wyliczeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
