---
title: ICorDebugModule2::ApplyChanges — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860b87b09ee487f893a1bba2aaa34292c50ffcb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764339"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges — Metoda
Ma zastosowanie zmian w metadanych i zmiany w kodzie języka intermediate language (MSIL) firmy Microsoft do uruchomionego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbMetadata`  
 [in] Rozmiar w bajtach metadanych delta.  
  
 `pbMetadata`  
 [in] Bufor, który zawiera metadane delta. Adres buforu jest zwracana z [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metody.  
  
 Względnych adresów wirtualnych (RVA) w metadanych powinna być określona względem początku kodu MSIL.  
  
 `cbIL`  
 [in] Rozmiar w bajtach, zmian kodu MSIL.  
  
 `pbIL`  
 [in] Bufor, który zawiera zaktualizowany kod MSIL.  
  
## <a name="remarks"></a>Uwagi  
 `pbMetadata` Parametr jest w formacie metadanych specjalne różnicowej (jako dane wyjściowe przez [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` Trwa poprzedniego metadanych jako podstawa oraz opis poszczególnych zmian do zastosowania do tej bazy.  
  
 Z kolei `pbIL[`] parametr zawiera nowy język MSIL dla zaktualizowanej metody i mają na celu całkowitego zastąpienia poprzedniego MSIL dla tej metody  
  
 Gdy delta MSIL i metadane zostały utworzone w pamięci w debugerze, debuger wywołuje `ApplyChanges` wysyła zmiany na środowisko uruchomieniowe języka wspólnego (CLR). Środowisko uruchomieniowe aktualizuje jego tabel metadanych, umieszcza nowe MSIL w procesie i konfiguruje kompilacji just-in-time (JIT) nowego języka MSIL. Jeśli zmiany zostały zastosowane, należy wywołać debugera [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) Aby przygotować się do edycji następnej sesji. Debuger może następnie kontynuować procesu.  
  
 Zawsze, gdy wywołuje debugera `ApplyChanges` w module, który zawiera metadane delta, powinien także wywołać [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) metadanymi zmian na wszystkie kopie w metadanych tego modułu, z wyjątkiem kopiowania używany do emitowania zmiany. Jeśli kopia metadanych jakiś sposób stanie się poza zsynchronizowane z metadanymi rzeczywiste, debuger zawsze możesz Pozbywać się kopii i uzyskać nową kopię.  
  
 Jeśli `ApplyChanges` metoda nie powiedzie się, debugowania sesji jest w nieprawidłowym stanie i musi zostać uruchomiony ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
