---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053419"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Tworzy inny nieprzetworzony moduł wyliczający urządzenia wejściowe z tym samym stanem co bieżący moduł wyliczający, aby wykonać iterację na tej samej liście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppenum`  
  
 określoną Adres zmiennej wyjściowej, która odbiera wskaźnik interfejsu [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) . Jeśli metoda nie powiedzie się, wartość tej zmiennej wyjściowej jest niezdefiniowana.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK Ta metoda obsługuje standardowe wartości zwracane E_INVALIDARG, E_OUTOFMEMORY i E_UNEXPECTED.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia zapisanie punktu w sekwencji wyliczenia w celu powrotu do tego punktu w późniejszym czasie. Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający niezależnie od pierwszego modułu wyliczającego.
