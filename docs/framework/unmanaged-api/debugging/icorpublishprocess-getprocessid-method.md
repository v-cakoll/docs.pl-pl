---
title: ICorPublishProcess::GetProcessID — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 4cc6bbde2c7367c1109ca73e66f2670a56b2cdbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790557"
---
# <a name="icorpublishprocessgetprocessid-method"></a>ICorPublishProcess::GetProcessID — Metoda
Pobiera identyfikator systemu operacyjnego dla tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pid`  
 określoną Wskaźnik do identyfikatora procesu reprezentowanego przez ten obiekt [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishProcess, interfejs](icorpublishprocess-interface.md)
