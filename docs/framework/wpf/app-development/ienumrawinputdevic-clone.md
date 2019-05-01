---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949594"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppenum`  
  
 [out] Adres zmiennej danych wyjściowych, który odbiera [ienumrawinputdevice —](ienumrawinputdevice.md) wskaźnika interfejsu. Jeśli metoda zakończy się niepowodzeniem, wartość tej zmiennej danych wyjściowych jest niezdefiniowane.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT: Ta metoda obsługuje standardowe wartości zwracane E_INVALIDARG E_OUTOFMEMORY i wartość E_UNEXPECTED.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia rejestrowanie punkt w kolejności wyliczenia, aby można było powrócić do tego punktu w późniejszym czasie. Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający, niezależnie od pierwszego modułu wyliczającego.
