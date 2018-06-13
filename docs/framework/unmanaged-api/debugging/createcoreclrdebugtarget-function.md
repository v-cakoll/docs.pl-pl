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
ms.openlocfilehash: a957eb6907b55fe948d696a6a25076c3950f7381
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402978"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget — Funkcja
Tworzy połączenie debugera serwer proxy, który jest uruchomiony na komputerze zdalnym i zwraca [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiektu, który może służyć do badania uruchomione procesy i załadować środowisk uruchomieniowych na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAddress`  
 [in] Adres IPv4 maszynę docelową zdalnego.  
  
 `ppTarget`  
 [out] Wskaźnik na wskaźnik do [icoreclrdebugtarget —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) obiektu, który zostanie utworzony.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 CLRs procesu został pomyślnie określana i odpowiednie dojścia tablice ścieżki zostały prawidłowo wypełnione.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci do `ppTarget`.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Inne błędy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
