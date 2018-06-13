---
title: ISymUnmanagedReader::GetVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74df7ee71fc541c35bc393f637ad1d7b9f7aa2a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425529"
---
# <a name="isymunmanagedreadergetvariables-method"></a>ISymUnmanagedReader::GetVariables — Metoda
Zwraca wartość zmiennej nie lokalnego na jego nadrzędny i nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] Element nadrzędny zmiennej.  
  
 `cVars`  
 [in] Rozmiar `pVars` tablicy.  
  
 `pcVars`  
 [out] Wskaźnik do zmiennej, która odbiera liczba zmiennych zwracane w `pVars`.  
  
 `pVars`  
 [out] Wskaźnik do zmiennej, która odbiera zmienne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
