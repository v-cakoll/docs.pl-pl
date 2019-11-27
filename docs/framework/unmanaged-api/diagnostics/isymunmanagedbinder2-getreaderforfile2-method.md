---
title: ISymUnmanagedBinder2::GetReaderForFile2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: 756ba2e71ca2e3e817a0a8b89165bb807368c1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449334"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 — Metoda
Podanym interfejsem metadanych i nazwą pliku zwraca poprawny interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) , który odczytuje symbole debugowania skojarzone z modułem.  
  
 Ta metoda zapewnia bardziej rozległe wyszukiwanie pliku bazy danych programu (PDB) niż Metoda [ISymUnmanagedBinder:: GetReaderForFile —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 podczas Wskaźnik do interfejsu importowania metadanych.  
  
 `fileName`  
 podczas Wskaźnik do nazwy pliku.  
  
 `searchPath`  
 podczas Wskaźnik do ścieżki wyszukiwania.  
  
 `searchPolicy`  
 podczas Wartość wyliczenia [CorSymSearchPolicyAttributes —](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) , która określa zasady, które mają być używane podczas wyszukiwania czytnika symboli.  
  
 `pRetVal`  
 określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="remarks"></a>Uwagi  
 Ta wersja metody może wyszukiwać plik PDB w obszarach innych niż bezpośrednio obok modułu. Zasady wyszukiwania można kontrolować, łącząc [CorSymSearchPolicyAttributes —](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Na przykład `AllowReferencePathAccess | AllowSymbolServerAccess` wyszukuje plik PDB obok pliku wykonywalnego i na serwerze symboli, ale nie wysyła zapytania do rejestru ani nie używa ścieżki w pliku wykonywalnym. Jeśli podano parametr `searchPath`, te katalogi będą zawsze przeszukiwane.  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedBinder2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [GetReaderForFile, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
