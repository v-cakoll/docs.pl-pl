---
title: CustomDumpItem — Struktura
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616440"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem — Struktura
Opisuje element, który ma zostać dodany do niestandardowego zrzutu w raporcie o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`itemKind`|Wartość [ECustomDumpItemKind —](ecustomdumpitemkind-enumeration.md) , która wskazuje rodzaj elementu, który ma zostać dodany.|  
|`pReserved`|Obecnie nie jest używany. Wszelkie elementy dodawane do Unii nie mogą być większe niż rozmiar wskaźnika. Jeśli `struct` jest wymagany, należy przydzielić go oddzielnie i wskazać.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRErrorReportingManager:: BeginCustomDump —](iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr typu `CustomDumpItem` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](hosting-structures.md)
