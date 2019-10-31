---
title: StrongNameTokenFromAssemblyEx — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104245"
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx — Funkcja
Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameTokenFromAssemblyEx —](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Ścieżka do przenośnego pliku wykonywalnego (PE) dla zestawu.  
  
 `ppbStrongNameToken`  
 określoną Zwrócony token silnej nazwy.  
  
 `pcbStrongNameToken`  
 określoną Rozmiar (w bajtach) tokenu silnej nazwy.  
  
 `ppbPublicKeyBlob`  
 określoną Zwrócony klucz publiczny.  
  
 `pcbPublicKeyBlob`  
 określoną Rozmiar (w bajtach) klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to skrócona postać klucza publicznego. Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu. Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.  
  
 Po pobraniu klucza i utworzeniu tokenu należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.  
  
 Jeśli funkcja `StrongNameTokenFromAssemblyEx` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameTokenFromAssemblyEx, metoda](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [StrongNameTokenFromAssembly, metoda](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
