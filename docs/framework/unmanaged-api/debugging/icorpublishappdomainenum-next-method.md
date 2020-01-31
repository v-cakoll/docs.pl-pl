---
title: ICorPublishAppDomainEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: c8866e98be0dd064138acdf5e0f6fb9c339fb3d2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790647"
---
# <a name="icorpublishappdomainenumnext-method"></a>ICorPublishAppDomainEnum::Next — Metoda
Pobiera określoną liczbę domen aplikacji, które aktualnie istnieją w procesie, rozpoczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba elementów, które mają zostać pobrane.  
  
 `objects`  
 określoną Wskaźnik do tablicy pobranych obiektów [ICorPublishAppDomain](icorpublishappdomain-interface.md) , z których każdy reprezentuje domenę aplikacji.  
  
 `pceltFetched`  
 określoną Wskaźnik na liczbę domen aplikacji, które faktycznie zostały zwrócone. Ta wartość może być równa null, jeśli `celt`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishAppDomainEnum, interfejs](icorpublishappdomainenum-interface.md)
