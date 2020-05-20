---
title: ICorPublishProcess::IsManaged — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421101"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged — Metoda
Pobiera wartość wskazującą, czy proces, do którego odwołuje się ten [ICorPublishProcess](icorpublishprocess-interface.md) , ma znany kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbManaged`  
 określoną Wskaźnik do wartości logicznej wskazującej, czy proces ma kod zarządzany. Wartość jest w `true` przypadku, gdy proces ma kod zarządzany; w przeciwnym razie `false` .  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ bieżąca wersja programu `ICorPublishProcess` zezwala na dostęp tylko do procesów, które mają kod zarządzany, `IsManaged` zawsze zwraca `true` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishProcess — Interfejs](icorpublishprocess-interface.md)
