---
title: StrongNameHashSize — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53384a5aa7f8d11f868057f892f7b60aac2e9f02
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799041"
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize — Funkcja
Pobiera rozmiar buforu wymagany dla skrótu przy użyciu określonego algorytmu wyznaczania wartości skrótu.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameHashSize —](../hosting/iclrstrongname-strongnamehashsize-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ulHashAlg`  
 podczas Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.  
  
 `pcbSize`  
 określoną Zwrócony rozmiar buforu w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameHashSize`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameHashSize, metoda](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
