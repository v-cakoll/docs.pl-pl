---
title: ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0ce6a207f2a7862b0b49f1e68cda9528aa03ca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667534"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda
Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym. Tę metodę można wywoływać wielokrotnie dla zmiennej o tej samej nazwie, który ma wiele domów w całym zakresie. W takim jednak wartości `startOffset` i `endOffset` parametry nie mogą się nakładać.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Lokalna nazwa zmiennej.  
  
 `attributes`  
 [in] Lokalne atrybuty zmiennej.  
  
 `sigToken`  
 [in] Token metadanych podpisu.  
  
 `addrKind`  
 [in] Typ adresu.  
  
 `addr1`  
 [in] Pierwszy adres specyfikację parametru.  
  
 `addr2`  
 [in] Drugi adres specyfikację parametru.  
  
 `addr3`  
 [in] Trzeci adres specyfikację parametru.  
  
 `startOffset`  
 [in] Przesunięcie początku dla zmiennej. Ten parametr jest opcjonalny. Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres. Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.  
  
 `endOffset`  
 [in] Przesunięcie zakończenia dla zmiennej. Ten parametr jest opcjonalny. Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres. Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
