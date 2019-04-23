---
title: COR_NATIVE_LINK — Struktura
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7024140ed9b870b5db38dba7e9b13321dd37386a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157589"
---
# <a name="cornativelink-structure"></a>COR_NATIVE_LINK — Struktura
Zawiera informacje, które jest używane do łączenia kodu natywnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`m_linkType`|Typ, które mają być łączone w kodzie natywnym. Ta wartość jest jednym z [cornativelinktype —](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) wartości.|  
|`m_flags`|Flagi używane przez konsolidator, podczas łączenia kodu natywnego. Ta wartość jest jednym z [cornativelinkflags —](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) wartości.|  
|`m_entryPoint`|Token metadanych MemberRef, który reprezentuje punkt wejścia. Format jest `lib:entrypoint`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags, wyliczenie](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
