---
title: ISymUnmanagedWriter::DefineLocalVariable — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6f8b896d50bb659897291d7bf85e836482611a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428989"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable — Metoda
Definiuje pojedynczą zmienną w bieżącym zakresie leksykalne. Tę metodę można wywoływać wielokrotnie dla zmiennej o tej samej nazwie, który ma wiele domach w całym zakresie. W tym przypadku jednak wartości `startOffset` i `endOffset` parametrów nie może nakładać się na.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Wskaźnik do `WCHAR` definiuje nazwę zmiennej lokalnej.  
  
 `attributes`  
 [in] Atrybuty zmiennej lokalnej.  
  
 `cSig`  
 [in] A `ULONG32` rozmiar w bajtach, który wskazuje z `signature` buforu.  
  
 `signature`  
 [in] Zmienna podpisu lokalnego.  
  
 `addrKind`  
 [in] Typ adresu.  
  
 `addr1`  
 [in] Pierwszy adres Specyfikacja parametru.  
  
 `addr2`  
 [in] Drugi adres Specyfikacja parametru.  
  
 `addr3`  
 [in] Trzeci adres Specyfikacja parametru.  
  
 `startOffset`  
 [in] Przesunięcie początku zmiennej. Ten parametr jest opcjonalny. Jeśli jest 0, ten parametr jest ignorowany i zmienna jest zdefiniowana w całym całego zakresu. Jeśli wartość niezerową, zmiennej spełnia przesunięcia bieżącego zakresu.  
  
 `endOffset`  
 [in] Przesunięcie zakończenia dla zmiennej. Ten parametr jest opcjonalny. Jeśli jest 0, ten parametr jest ignorowany i zmienna jest zdefiniowana w całym całego zakresu. Jeśli wartość niezerową, zmiennej spełnia przesunięcia bieżącego zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [DefineGlobalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [DefineLocalVariable2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
