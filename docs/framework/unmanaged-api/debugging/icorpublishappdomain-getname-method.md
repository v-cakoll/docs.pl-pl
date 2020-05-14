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
ms.openlocfilehash: e95f96847c6e069758362fb6febc28dc31911bc9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396298"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName — Metoda
Pobiera nazwę domeny aplikacji reprezentowanej przez ten [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
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
 podczas Rozmiar `szName` tablicy.  
  
 `pcchName`  
 określoną Wskaźnik do liczby znaków dwubajtowych, w tym znak null, zwracany w `szName` tablicy.  
  
 `szName`  
 określoną Tablica, w której ma zostać przechowana nazwa.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `szName` jest inna niż null, `GetName` Metoda kopiuje do. do `cchName` znaków (w tym terminator wartości null) `szName` . Jeśli zwracana jest wartość inna niż null `pcchName` , rzeczywista liczba znaków w nazwie (łącznie z terminatorem wartości null) jest przechowywana w `szName` tablicy.  
  
 `GetName`Metoda zwraca S_OK HRESULT, niezależnie od liczby skopiowanych znaków.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishAppDomain — Interfejs](icorpublishappdomain-interface.md)
