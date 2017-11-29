---
title: "ICorPublishAppDomain::GetName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9807f914c767cc212bf97d83042e76d42a3d9440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName — Metoda
Pobiera nazwę domeny aplikacji, która jest reprezentowana przez to [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Rozmiar `szName` tablicy.  
  
 `pcchName`  
 [out] Wskaźnik do liczby znaki dwubajtowe, w tym znakiem null zwracane w `szName` tablicy.  
  
 `szName`  
 [out] Tablica do przechowywania nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `szName` jest różna od null, `GetName` metoda kopiuje do `cchName` znaków (włącznie z terminatorem null) do `szName`. Jeśli inne niż null, jest zwracany w `pcchName`, rzeczywista liczba znaków w polu Nazwa (włącznie z terminatorem null) są przechowywane w `szName` tablicy.  
  
 `GetName` Metoda zwróci wartość HRESULT S_OK niezależnie od tego, ile znaków zostały skopiowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorPublishAppDomain — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
