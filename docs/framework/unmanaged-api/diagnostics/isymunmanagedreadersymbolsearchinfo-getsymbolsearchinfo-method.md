---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628d6fac45b046d9e8f26ad8777c38450da27a1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427421"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a>ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda
Pobiera informacje o wyszukiwaniu symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cSearchInfo`  
 [in] A `ULONG32` wskazuje, że rozmiar `rgpSearchInfo`.  
  
 `pcSearchInfo`  
 [out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.  
  
 `rgpSearchInfo`  
 [out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReaderSymbolSearchInfo, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
