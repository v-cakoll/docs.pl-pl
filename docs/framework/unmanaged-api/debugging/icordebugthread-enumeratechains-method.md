---
title: ICorDebugThread::EnumerateChains — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: 711fccd65379bc3e5e178869e7220dd84fd07fbe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379704"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains — Metoda
Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym obiekcie ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChains`  
 określoną Wskaźnik do adresu `ICorDebugChainEnum` obiektu, który umożliwia wyliczenie wszystkich łańcuchów stosu w tym wątku, rozpoczynając od aktywnego (czyli ostatniego) łańcucha.  
  
## <a name="remarks"></a>Uwagi  
 Łańcuch stosu reprezentuje stos wywołań fizycznych wątku. W następujących sytuacjach należy utworzyć granicę łańcucha stosu:  
  
- Przejście z zarządzanego lub niezarządzanego lub niezarządzanego do zarządzanego.  
  
- Przełącznik kontekstu.  
  
- Debuger przejmowanie wątku użytkownika.  
  
 W prostym przypadku wątku, w którym działa kod zarządzany całkowicie w pojedynczym kontekście, między wątkami i łańcuchami stosu będzie nadana korespondencja typu jeden do jednego.  
  
 Debuger może chcieć zmienić rozmieszczenie stosów wywołań fizycznych wszystkich wątków na stosy wywołań logicznych. Obejmuje to posortowanie wszystkich łańcuchów wątków według ich relacji wywołujących/wywoływanych i przegrupowanie ich.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
