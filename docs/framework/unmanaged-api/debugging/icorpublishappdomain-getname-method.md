---
title: ICorPublishAppDomain::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5de74b52caee27a1a12cff4a7f9165a07e961ce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993583"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName — Metoda
Pobiera nazwę domeny aplikacji, który jest reprezentowany przez ten [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Rozmiar `szName` tablicy.  
  
 `pcchName`  
 [out] Wskaźnik do liczby znaków dwubajtowych znakiem zerowym, zwracane w tym `szName` tablicy.  
  
 `szName`  
 [out] Tablica do przechowywania nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `szName` jest różna od null, `GetName` metoda kopiuje do `cchName` znaków (łącznie z terminatorem null) do `szName`. Jeśli zwracana jest inna niż null w `pcchName`, rzeczywista liczba znaków w nazwie (łącznie z terminatorem null) są przechowywane w `szName` tablicy.  
  
 `GetName` Metoda zwróci wartość HRESULT S_OK, niezależnie od tego, ile znaków zostały skopiowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishAppDomain, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
