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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 930d56fcfe7cf0d2a128c2068e724b85a224b3fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568923"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem — Struktura
Opis elementu do dodania do niestandardowych zrzutu w raportowaniu błędów.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`itemKind`|[Ecustomdumpitemkind —](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) wartość wskazującą rodzaj elementu do dodania.|  
|`pReserved`|Obecnie nieużywane. Wszystkie elementy dodane do Unii musi być większy niż rozmiar wskaźnika. Jeśli `struct` jest wymagane, należy przydzielić je oddzielnie i wskaż go.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrerrorreportingmanager::begincustomdump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr typu `CustomDumpItem`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
