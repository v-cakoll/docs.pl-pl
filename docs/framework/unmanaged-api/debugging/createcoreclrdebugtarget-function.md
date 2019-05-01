---
title: CreateCoreClrDebugTarget — Funkcja
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48ce5381c745669b813f5b28d801add7daba7825
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965844"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget — Funkcja
Tworzy połączenie z serwerem proxy debugera, jest uruchomiona na maszynie zdalnej, która zwraca [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiekt, który może służyć do kwerendy, uruchomione procesy i załadować środowisk wykonawczych na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAddress`  
 [in] Adres IPv4 komputera zdalnego docelowego.  
  
 `ppTarget`  
 [out] Wskaźnik do wskaźnika do [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiektu, który zostanie utworzony.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 CLRs procesu został pomyślnie określana i odpowiednie dojścia i tablice ścieżki zostały prawidłowo wypełnione.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci do `ppTarget`.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Inne błędy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
