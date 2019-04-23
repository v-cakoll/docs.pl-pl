---
title: ICLRDataTarget::GetPointerSize — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73645265821d5854776e412f8eb0f33b36db00d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130497"
---
# <a name="iclrdatatargetgetpointersize-method"></a>ICLRDataTarget::GetPointerSize — Metoda
Pobiera rozmiar w bajtach, typu wskaźnika, który używa procesu docelowego. Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pointerSize`  
 [out] Wskaźnik do wartości całkowitej, która określa rozmiar w bajtach, wskaźnik w procesie docelowym.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
