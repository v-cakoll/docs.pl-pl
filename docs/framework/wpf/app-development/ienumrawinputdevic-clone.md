---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545349"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Tworzy inny moduł wyliczający raw urządzenia wejściowego z takim samym stanie, aby jako bieżącego modułu wyliczającego, aby przejść przez tę samą listę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
  
 [out] Adresu zmiennej danych wyjściowych, który odbiera [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) wskaźnika interfejsu. Jeśli metoda zakończy się niepowodzeniem, wartość tej zmiennej danych wyjściowych jest niezdefiniowany.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Wynik HRESULT: Ta metoda obsługuje standardowe wartości zwracanych E_INVALIDARG E_OUTOFMEMORY i E_UNEXPECTED.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia rejestrowanie punktu w sekwencji wyliczenie aby powrócić do tego punktu w późniejszym czasie. Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający niezależnie od pierwszego modułu wyliczającego.
