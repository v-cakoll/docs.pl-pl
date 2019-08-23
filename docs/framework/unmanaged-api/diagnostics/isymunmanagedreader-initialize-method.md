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
ms.openlocfilehash: f2dceeb2f0b3aa9f3147157e77087dffbf2d5f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939027"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize — Metoda
Inicjuje czytnik symboli z interfejsem importera metadanych, z którym zostanie skojarzony ten czytnik, wraz z nazwą pliku modułu.  
  
> [!NOTE]
> Tę metodę można wywołać tylko raz i muszą one zostać wywołane przed innymi metodami czytnika.  
  
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
 podczas Interfejs programu do importowania metadanych, z którym ten czytnik zostanie skojarzony.  
  
 `filename`  
 podczas Nazwa pliku modułu. Zamiast tego można użyć `pIStream` parametru.  
  
 `searchPath`  
 podczas Ścieżka do wyszukania. Ten parametr jest opcjonalny.  
  
 `pIStream`  
 podczas Strumień pliku używany jako alternatywa dla parametru filename.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie, E_FAIL lub inny kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko jeden z `filename` `pIStream` parametrów lub. `searchPath` Parametr jest opcjonalny.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówki** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
