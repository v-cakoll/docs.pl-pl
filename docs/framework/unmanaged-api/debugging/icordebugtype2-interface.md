---
title: ICorDebugType2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 0e480db953131d7771e493a8f367154a7d17dada
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396630"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2, interfejs
Rozszerza interfejs ICorDebugType w celu pobrania identyfikatora typu podstawowego lub złożonego (zdefiniowanego przez użytkownika).  
  
## <a name="methods"></a>Metody  
  
|Metoda||  
|------------|-|  
|[GetTypeID, metoda](icordebugtype2-gettypeid-method.md)|Pobiera [COR_TYPEID](cor-typeid-structure.md) dla tego typu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest logicznym rozszerzeniem interfejsu ICorDebugType.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu ilustruje użycie metody [ICorDebugType2:: GetTypeId](icordebugtype2-gettypeid-method.md) .  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
