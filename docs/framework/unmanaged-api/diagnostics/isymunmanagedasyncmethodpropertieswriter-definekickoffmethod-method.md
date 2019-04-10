---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226615"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda
Ustawia metodę początkową, która inicjuje operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
