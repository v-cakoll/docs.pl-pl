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
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179218"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget — Funkcja
Tworzy połączenie z serwerem proxy debugera, który jest uruchomiony na komputerze zdalnym i zwraca [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) obiektu, który może służyć do wykonywania zapytań uruchomionych procesów i załadowanych runtimes na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAddress`  
 [w] adres IPv4 zdalnego komputera docelowego.  
  
 `ppTarget`  
 [na zewnątrz] Wskaźnik do wskaźnika do [obiektu ICoreClrDebugTarget,](icoreclrdebugtarget-interface.md) który zostanie utworzony.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Liczba clr w procesie została pomyślnie określona, a odpowiednie tablice dojścia i ścieżki zostały poprawnie wypełnione.  
  
 E_outofmemory  
 Nie można przydzielić `ppTarget`wystarczającej ilości pamięci dla pliku .  
  
 E_FAIL (lub inne E_ kody zwrotne)  
 Inne awarie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje .NET Framework:** 3.5 SP1
