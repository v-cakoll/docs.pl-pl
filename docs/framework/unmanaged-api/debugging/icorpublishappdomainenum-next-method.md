---
title: "ICorPublishAppDomainEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79b9ad5711ac1d0166a7ad328cc227f17780476c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomainenumnext-method"></a>ICorPublishAppDomainEnum::Next — Metoda
Pobiera określoną liczbę domen aplikacji, które obecnie istnieją w procesie, zaczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów do pobrania.  
  
 `objects`  
 [out] Wskaźnik do tablicy pobrać [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) obiektów, z których każdy reprezentuje domeny aplikacji.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby domen aplikacji faktycznie zwracane. Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorPublishAppDomainEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
