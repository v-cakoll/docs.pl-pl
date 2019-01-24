---
title: ISymUnmanagedWriter::DefineField — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03c0a9d7315f5158948701d4322887104f0844c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603667"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField — Metoda
Definiuje pojedynczej zmiennej, która nie znajduje się w metody. Ta metoda jest używana w przypadku niektórych pól w klasach, pola bitowe i tak dalej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] Typ metadanych lub metoda tokenu.  
  
 `name`  
 [in] Nazwa pola.  
  
 `attributes`  
 [in] Atrybuty pól.  
  
 `cSig`  
 [in] A `ULONG32` oznacza to rozmiar, w postaci, buforu, muszą zawierać podpis pola.  
  
 `signature`  
 [in] Tablica sygnatury pól.  
  
 `addrKind`  
 [in] Typ adresu.  
  
 `addr1`  
 [in] Pierwszy adres dotyczyło pola.  
  
 `addr2`  
 [in] Drugi adres dotyczyło pola.  
  
 `addr3`  
 [in] Trzeci adres dotyczyło pola.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
