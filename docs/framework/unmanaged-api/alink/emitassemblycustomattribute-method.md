---
title: EmitAssemblyCustomAttribute — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67073f04cfe981dd383369029d9a4b436929a0a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117848"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute — Metoda
Wywołać można ustawić na poziomie zestawu atrybutów niestandardowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu.  
  
 `FileToken`  
 Plik, który defiles atrybutu. Może mieć wartości NULL, jeśli `AssemblyID` nie wskazuje niepowiązanych modułu netmodule.  
  
 `tkType`  
 Typ atrybutu niestandardowego.  
  
 `pCustomValue`  
 Niestandardowa wartość danych.  
  
 `cbCustomValue`  
 Długość danych niestandardowych wartości.  
  
 `bSecurity`  
 Wartość TRUE, jeśli atrybut niestandardowy jest powiązany do podpisywania zestawu.  
  
 `bAllowMulti`  
 Wartość TRUE, jeśli wiele atrybutów, które mają być emitowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także

- [IALink — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink — interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
