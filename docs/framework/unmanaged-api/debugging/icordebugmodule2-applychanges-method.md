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
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges — Metoda
Stosuje zmiany w metadanych i zmian w kodzie języka pośredniego (MSIL) firmy Microsoft do uruchomionego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbMetadata`  
 [in] Rozmiar w bajtach metadanych delta.  
  
 `pbMetadata`  
 [in] Bufor zawierający metadane delta. Adres buforu jest zwracana z [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metody.  
  
 Względne wirtualnych adresów (RVAs) w metadanych powinna być określona względem początku kodu MSIL.  
  
 `cbIL`  
 [in] Rozmiar w bajtach różnicowych kod MSIL.  
  
 `pbIL`  
 [in] Buforu, który zawiera zaktualizowanego kodu MSIL.  
  
## <a name="remarks"></a>Uwagi  
 `pbMetadata` Parametru jest w formacie metadanych delta specjalnych (jak wyjściowych przez [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` Trwa poprzednie metadanych jako podstawa oraz opis poszczególnych zmian do zastosowania do tej bazy.  
  
 Z kolei `pbIL[`] parametr zawiera nowe MSIL dla zaktualizowanej metody i ma całkowicie zastąpić poprzednie MSIL dla tej metody  
  
 Gdy delta MSIL i metadanych zostały utworzone w pamięci debugera, debuger wywołuje `ApplyChanges` Aby wysłać zmiany do środowisko uruchomieniowe języka wspólnego (CLR). Środowisko uruchomieniowe aktualizuje jego tabele metadanych, umieszcza nowe MSIL w procesie i konfiguruje just in time (JIT) zbiór nowych MSIL. Podczas zmiany zostały zastosowane, debuger powinien wywoływać [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) do przygotowania do następnej sesji edytowania. Debuger może następnie kontynuować proces.  
  
 Zawsze, gdy debuger wywołuje `ApplyChanges` na module, który ma metadane zmian, należy także wywołać [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) metadanymi zmian na wszystkich jego kopie metadanych tego modułu, z wyjątkiem kopii używany do wysyłania zmiany. Jeśli kopia metadanych jakiś sposób staje się poza synchronizacja z metadanymi rzeczywiste debuger zawsze wyrzucać tej kopii i uzyskać nową kopię.  
  
 Jeśli `ApplyChanges` metoda zawiedzie, debugowania sesja jest w nieprawidłowym stanie i musi zostać ponownie uruchomione.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
