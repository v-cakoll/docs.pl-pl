---
title: SetAssemblyFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 006360203518f74adb964634af52505a71d51473
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587102"
---
# <a name="setassemblyfile-method"></a>SetAssemblyFile — Metoda
Przypisuje nazwę zestawu, który ma zostać utworzony. Nie do wykorzystania podczas produkowania niepowiązanych modułów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFilename`  
 W pełni kwalifikowana nazwa pliku manifestu.  
  
 `pEmitter`  
 Wskaźnik do [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejsu.  
  
 `afFlags`  
 Flagi zgodnie z definicją w [assemblyflags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Wskaźnik do Identyfikatora Wynikowy zestaw.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz także
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
