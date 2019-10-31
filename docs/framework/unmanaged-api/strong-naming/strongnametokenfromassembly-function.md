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
ms.openlocfilehash: 6b9eca3f2f0267870866874ea27dc65812795f41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121131"
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
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to skrócona postać klucza publicznego. Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu. Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.  
  
 Po utworzeniu tokenu należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.  
  
 Jeśli funkcja `StrongNameTokenFromAssembly` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameTokenFromAssembly, metoda](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx, metoda](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
