---
title: "ICorDebugRemoteTarget::GetHostName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget.GetHostName
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2af5d75145b9fdd2d370b76f798c5e350d8bec50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName — Metoda
Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 zdalnego debugowania maszyny docelowej. Protokół IPv6 nie jest obsługiwany w tej chwili.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchHostName`  
 [in] Rozmiar w znaków z `szHostName` buforu. Jeśli ten parametr ma wartość 0 (zero), `szHostName` może mieć wartości null.  
  
 `pcchHostName`  
 [out] Liczba znaków, włącznie z terminatorem null, nazwa hosta lub adres IP. Ten parametr może mieć wartości null.  
  
 `szHostName`  
 [out] Bufor, który zawiera nazwę hosta lub adres IP.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie zwrócono nazwę hosta lub adres IP.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można zwrócić nazwę hosta lub adres IP.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowany przez twórcę debugera. Należy wykonać wiele modelu wywołania: przy pierwszym wywołaniu wywołujący wartości null zarówno `cchHostName` i `szHostName`, i `pcchHostName` zwraca rozmiar buforu wymagane. Na drugie wywołanie, rozmiar, który został wcześniej zostały zwrócone jest przekazywany w `cchHostName`, i odpowiednio rozmiar buforu jest przekazywany w `szHostName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRemoteTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
