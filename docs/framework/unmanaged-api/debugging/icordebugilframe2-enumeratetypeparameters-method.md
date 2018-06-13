---
title: ICorDebugILFrame2::EnumerateTypeParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a0c23c066a6f704c4dfcfbe254e91ab3bc5817e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416244"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters — Metoda
Pobiera obiekt ICorDebugTypeEnum zawierający <xref:System.Type> parametrów do tej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 Wskaźnik do adresu ICorDebugTypeEnum obiektu interfejs, umożliwiający wyliczenie parametrów typu.  
  
 Parametry typu zawierają parametrów typu klasy (jeśli istnieją) następuje parametr typu metody (jeśli istnieje).  
  
## <a name="remarks"></a>Uwagi  
 Użyj [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) metodę, aby określić, ile parametrów typu klasy i metody ta lista zawiera parametry typu.  
  
 Parametry typu nie są zawsze dostępne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
