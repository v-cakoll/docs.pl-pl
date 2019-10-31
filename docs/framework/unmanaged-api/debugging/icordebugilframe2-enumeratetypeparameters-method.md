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
ms.openlocfilehash: 715ff5d4a06b53361d550f04e5154023d0b641bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095121"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters — Metoda
Pobiera obiekt ICorDebugTypeEnum, który zawiera <xref:System.Type> parametry w tej ramce.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 Wskaźnik do adresu obiektu interfejsu ICorDebugTypeEnum, który umożliwia Wyliczenie parametrów typu.  
  
 Lista parametrów typu zawiera parametry typu klasy (jeśli istnieją), a następnie parametry typu metody (jeśli istnieją).  
  
## <a name="remarks"></a>Uwagi  
 Użyj metody [IMetaDataImport2:: EnumGenericParams —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) , aby określić, ile parametrów typu klasy i parametrów typu metody ta lista zawiera.  
  
 Parametry typu nie są zawsze dostępne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
