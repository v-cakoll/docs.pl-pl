---
title: ISymUnmanagedWriter::DefineParameter — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b82415635980f5bd4e13e87a0a03ec5b7032bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777325"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter — Metoda
Definiuje pojedynczy parametr w bieżącej metodzie. Typ parametru jest pobierana z parametru pozycji (kolejny) w podpisie metody.  
  
 Parametry są definiowane w metadanych dla danej metody, nie trzeba je ponownie zdefiniować za pomocą tej metody. Czytelnicy symbol musi sprawdzić normalne metadane parametrów przed sprawdzeniem magazynu symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 [in] Nazwa parametru.  
  
 `attributes`  
 [in] Atrybuty parametru.  
  
 `sequence`  
 [in] Podpis parametru.  
  
 `addrKind`  
 [in] Typ adresu.  
  
 `addr1`  
 [in] Pierwszy adres specyfikację parametru.  
  
 `addr2`  
 [in] Drugi adres specyfikację parametru.  
  
 `addr3`  
 [in] Trzeci adres specyfikację parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
