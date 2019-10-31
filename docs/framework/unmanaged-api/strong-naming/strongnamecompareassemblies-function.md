---
title: StrongNameCompareAssemblies — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: adde52dddb63b83dcd7ff10703a43928d9601c92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140620"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies — Funkcja
Określa, czy dwa zestawy różnią się tylko sygnaturami silnej nazwy.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameCompareAssemblies —](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 podczas Ścieżka do pierwszego zestawu.  
  
 `wszAssembly2`  
 podczas Ścieżka do drugiego zestawu.  
  
 `pdwResult`  
 określoną Jedna z następujących wartości:  
  
- `SN_CMP_DIFFERENT` (0) — określa, że zestawy zawierają różne dane.  
  
- `SN_CMP_IDENTICAL` (1) — określa, że zestawy są dokładnie takie same, łącznie z ich sygnaturami i sumą kontrolną.  
  
- `SN_CMP_SIGONLY` (2) — określa, że zestawy różnią się tylko sygnaturą i sumą kontrolną.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Uwagi  
 Podpis silnej nazwy zestawu składa się z nazwy tekstu, wersji, kultury i tokenu klucza publicznego zestawu.  
  
 Jeśli funkcja `StrongNameCompareAssemblies` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameCompareAssemblies, metoda](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
