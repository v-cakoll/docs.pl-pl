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
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446508"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute — Metoda
Wywołanie ustawiania atrybutów niestandardowych na poziomie zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 Plik, który deplikuje atrybut. Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niepowiązanego modułu.  
  
 `tkType`  
 Typ atrybutu niestandardowego.  
  
 `pCustomValue`  
 Dane wartości niestandardowej.  
  
 `cbCustomValue`  
 Długość danych wartości niestandardowych.  
  
 `bSecurity`  
 Ma wartość TRUE, jeśli atrybut niestandardowy jest powiązany z podpisywaniem zestawu.  
  
 `bAllowMulti`  
 Ma wartość TRUE, jeśli wiele atrybutów ma być emitowanych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
