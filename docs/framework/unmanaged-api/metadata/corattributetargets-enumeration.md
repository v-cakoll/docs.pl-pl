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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fb1dff80fccc920540d370797441b3a019d766c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780912"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets — Wyliczenie
Określa elementy aplikacji, na których jest on prawidłowy, aby zastosować atrybut.  
  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`catAssembly`|Atrybut można stosować do zestawu.|  
|`catModule`|Atrybut można stosować do przenośnego pliku wykonywalnego modułu (.dll lub .exe).|  
|`catClass`|Atrybut można stosować do klasy.|  
|`catStruct`|Atrybut można stosować do struktury; oznacza to, że wartość typu.|  
|`catEnum`|Atrybut można stosować do wyliczenia.|  
|`catConstructor`|Atrybut można stosować do konstruktora.|  
|`catMethod`|Atrybut można stosować do metody.|  
|`catProperty`|Atrybut można stosować do właściwości.|  
|`catField`|Atrybut można stosować do pola.|  
|`catEvent`|Atrybut można stosować do zdarzenia.|  
|`catInterface`|Do interfejsu, można zastosować atrybutu.|  
|`catParameter`|Atrybut można stosować do parametru.|  
|`catDelegate`|Atrybut można stosować do delegata.|  
|`catGenericParameter`|Atrybut można stosować do parametru ogólnego.|  
|`catAll`|Atrybut można stosować do dowolnych aplikacji.|  
|`catClassMembers`|Atrybut można stosować do składowej klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `CorAttributeTargets` Wartości wyliczenia można łączyć za pomocą bitowej operacji lub można pobrać preferowanych kombinacji.  
  
 `CorAttributeTargets` Równoleżnikami zarządzanej <xref:System.AttributeTargets?displayProperty=nameWithType> wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
