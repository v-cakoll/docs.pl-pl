---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: fadf7b5526598f446eb7e49640bf4d43ec7395bf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354521"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Powoduje, że moduł wyliczający, aby pominąć następnego `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nie będzie zwracać tych elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
  
 [in] Liczba elementów do pominięcia.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT: S_OK, jeśli liczba elementów, które podano `celt`; W przeciwnym razie S_FALSE.
