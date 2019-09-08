---
title: StrongNameTokenFromAssembly — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71058a1ff82335b2a341904805d06738e662c296
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798872"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly — Funkcja
Tworzy token silnej nazwy z określonego pliku zestawu.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameTokenFromAssembly —](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Ścieżka do przenośnego pliku wykonywalnego (PE) dla zestawu.  
  
 `ppbStrongNameToken`  
 określoną Zwrócony token silnej nazwy.  
  
 `pcbStrongNameToken`  
 określoną Rozmiar (w bajtach) tokenu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to skrócona postać klucza publicznego. Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu. Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.  
  
 Po utworzeniu tokenu należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.  
  
 Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameTokenFromAssembly`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameTokenFromAssembly, metoda](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx, metoda](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
