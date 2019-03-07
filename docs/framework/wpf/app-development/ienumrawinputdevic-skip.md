---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: f7d7df77c54d4551025aa5a344c96083c263f455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467171"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Powoduje, że moduł wyliczający, aby pominąć następnego `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nie będzie zwracać tych elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
  
 [in] Liczba elementów do pominięcia.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT: S_OK, jeśli liczba elementów, które podano `celt`; W przeciwnym razie S_FALSE.
