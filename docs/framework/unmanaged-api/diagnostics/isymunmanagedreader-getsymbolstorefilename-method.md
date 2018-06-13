---
title: ISymUnmanagedReader::GetSymbolStoreFileName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b36f4007f286938169cc5d583908493916b9e6f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425343"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a>ISymUnmanagedReader::GetSymbolStoreFileName — Metoda
Zawiera nazwę pliku na dysku magazynu symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Rozmiar `szName` buforu.  
  
 `pcchName`  
 [out] Wskaźnik do zmiennej, która odbiera długość nazwy zwracane w `szName`, takie jak zakończenie wartości null.  
  
 `szName`  
 [out] Wskaźnik do zmiennej, która otrzymuje nazwę pliku w magazynie symboli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
