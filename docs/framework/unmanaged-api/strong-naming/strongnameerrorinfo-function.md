---
title: StrongNameErrorInfo — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
ms.openlocfilehash: d5eedc34b75d3a0c02969c06454b0f7ec942ed17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176945"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo — Funkcja
Pobiera ostatni kod błędu, który został podniesiony przez jedną z funkcji silnej nazwy.  
  
 Ta funkcja została przestarzała.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ostatni kod błędu COM ustawiony przez jedną z funkcji silnej nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Większość metod silnej nazwy `true` zwraca `false` prostą lub wskazanie pomyślnego zakończenia. `StrongNameErrorInfo` Funkcja służy do pobierania funkcji HRESULT, która określa ostatni błąd generowany przez funkcje silnej nazwy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
