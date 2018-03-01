---
title: "ISymUnmanagedReader::Initialize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize — Metoda
Inicjuje czytnika symboli z interfejsem importer metadanych, który tego czytnika zostanie skojarzona z, wraz z nazwą modułu.  
  
> [!NOTE]
>  Ta metoda może być wywołana tylko raz i musi zostać wywołana przed innymi metodami czytnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [in] Interfejs importer metadanych, z którą zostanie skojarzona tego czytnika.  
  
 `filename`  
 [in] Nazwa pliku modułu. Można użyć `pIStream` parametru zamiast tego.  
  
 `searchPath`  
 [in] Ścieżka do wyszukiwania. Ten parametr jest opcjonalny.  
  
 `pIStream`  
 [in] Strumień pliku używany jako alternatywę dla parametru filename.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba. `searchPath` Parametr jest opcjonalny.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
