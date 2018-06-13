---
title: SetAssemblyFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ade568889d1c0203115f160d855de8c598798196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403360"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 — Metoda
Ustawia opcje dla nowego zestawu i nazwa. Ta metoda zostanie wywołana podczas tworzenia modułów niepowiązanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFilename`  
 Nazwa pliku manifestu.  
  
 `pEmitter`  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejs dla tego pliku.  
  
 `afFlags`  
 Opcje reprezentowany przez [AssemblyFlags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Otrzymuje unikatowy identyfikator dla zestawu tworzona.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz też  
 [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
