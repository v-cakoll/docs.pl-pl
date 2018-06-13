---
title: ISymUnmanagedBinder3::GetReaderFromCallback — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f44d50f6736e0698fd876eedab78dbf41434af4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426319"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a>ISymUnmanagedBinder3::GetReaderFromCallback — Metoda
Zezwala użytkownikowi na wdrożenie lub podać za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback` Aby uzyskać informacje o debugowaniu katalogu z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [in] Wskaźnik do interfejsu importu metadanych.  
  
 `fileName`  
 [in] Wskaźnik do nazwy pliku.  
  
 `searchPath`  
 [in] Wskaźnik do ścieżki wyszukiwania.  
  
 `searchPolicy`  
 [in] Wartość [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) wyliczenia, która określa zasady, która ma być używane podczas wyszukiwania dla czytnika symboli.  
  
 `callback`  
 [in] Wskaźnik do funkcji wywołania zwrotnego.  
  
 `pRetVal`  
 [out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedBinder3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
