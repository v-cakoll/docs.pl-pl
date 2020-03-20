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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178406"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName — Metoda
Pobiera nazwę domeny aplikacji, która jest reprezentowana przez ten [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [w] Rozmiar tablicy. `szName`  
  
 `pcchName`  
 [na zewnątrz] Wskaźnik do liczby znaków szerokich, w tym znaku `szName` null, zwrócony w tablicy.  
  
 `szName`  
 [na zewnątrz] Tablica, w której ma być przechowywana nazwa.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `szName` metoda nie jest `GetName` null, metoda `cchName` kopiuje do znaków `szName`(w tym zerowy terminator) do . Jeśli w `pcchName`tablicy jest zwracana wartość null, rzeczywista liczba znaków w nazwie `szName` (w tym terminator zerowy) jest przechowywana w tablicy.  
  
 Metoda `GetName` zwraca S_OK HRESULT niezależnie od liczby znaków zostały skopiowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorPublishAppDomain, interfejs](icorpublishappdomain-interface.md)
