---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053374"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Instruuje moduł wyliczający, aby pominąć `celt` kolejne elementy w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nie zwróci tych elementów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
  
 podczas Liczba elementów, które mają zostać pominięte.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK S_OK, jeśli liczba dostarczonych elementów to `celt`; S_FALSE w inny sposób.
