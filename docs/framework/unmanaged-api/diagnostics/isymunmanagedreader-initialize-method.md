---
title: ISymUnmanagedReader::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1986ed730c6f0a1ba8a2d8e3c688e6872184da9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736754"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize — Metoda
Inicjuje czytnika symboli z interfejsem importera metadanych, które ten czytnik będzie skojarzona, wraz z nazwą pliku modułu.  
  
> [!NOTE]
>  Ta metoda może być wywołana tylko raz i musi zostać wywołana przed wszystkimi metodami czytnika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 [in] Interfejs importera metadanych za pomocą którego ten czytnik zostanie skojarzona.  
  
 `filename`  
 [in] Nazwa pliku modułu. Możesz użyć `pIStream` parametru zamiast tego.  
  
 `searchPath`  
 [in] Ścieżka do wyszukania. Ten parametr jest opcjonalny.  
  
 `pIStream`  
 [in] Strumień pliku używana jako alternatywa dla parametru filename.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko jeden z `filename` lub `pIStream` parametrów, nie obydwa. `searchPath` Parametr jest opcjonalny.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
