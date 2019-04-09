---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcd200b7fa431f193dd202c3c2a690aa22ec8e32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135190"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a>ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda
Pobiera metodę czytnika symboli, biorąc pod uwagę token metody oraz numer wersji edit-and-continue. Numery wersji są liczone od 1 i jest zwiększana za każdym razem, gdy metoda zmienia się w wyniku operacji Edytuj i Kontynuuj.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `token`  
 [in] Metoda token metadanych.  
  
 `version`  
 [in] Wersja metody.  
  
 `pRetVal`  
 [out] Wskaźnik do zwracanego [isymunmanagedmethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl. CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
