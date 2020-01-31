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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789192"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget — Funkcja
Tworzy połączenie z serwerem proxy debugera, który jest uruchomiony na komputerze zdalnym i zwraca obiekt [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , który może służyć do wykonywania zapytań dotyczących uruchomionych procesów i załadowanych środowiska uruchomieniowego na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAddress`  
 podczas Adres IPv4 zdalnej maszyny docelowej.  
  
 `ppTarget`  
 określoną Wskaźnik do wskaźnika do obiektu [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , który zostanie utworzony.  
  
## <a name="return-value"></a>Wartość zwrócona  
 S_OK  
 Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci dla `ppTarget`.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Inne błędy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Library:** mscordbi_macx86.dll  
  
 **.NET Framework wersje:** 3,5 SP1
