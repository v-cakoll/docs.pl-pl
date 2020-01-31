---
title: ICorDebugDataTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 9029d53872108bc1953fd22c584b6e01a6f3c7ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788866"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget — Interfejs
Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPlatform, metoda](icordebugdatatarget-getplatform-method.md)|Zawiera informacje na temat platformy, w tym architektury procesora i systemu operacyjnego, na których jest uruchomiony proces docelowy.|  
|[ReadVirtual, metoda](icordebugdatatarget-readvirtual-method.md)|Pobiera blok ciągłej pamięci zaczynający się od określonego adresu i zwraca go w dostarczonym buforze.|  
|[GetThreadContext, metoda](icordebugdatatarget-getthreadcontext-method.md)|Żąda bieżącego kontekstu wątku dla określonego wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugDataTarget` i jego metody mają następującą charakterystykę:  
  
- Usługi debugowania wywołują metody tego interfejsu w celu uzyskania dostępu do pamięci i innych danych w procesie docelowym.  
  
- Klient debugera musi zaimplementować ten interfejs stosownie do określonego celu (na przykład procesu na żywo lub zrzutu pamięci).  
  
- Metody `ICorDebugDataTarget` mogą być wywoływane tylko z metod zaimplementowanych w innych interfejsach `ICorDebug*`. Dzięki temu klient debugera ma kontrolę nad tym, który wątek jest wywoływany, i kiedy.  
  
- Implementacja `ICorDebugDataTarget` musi zawsze zwracać aktualne informacje o miejscu docelowym.  
  
 Proces docelowy powinien zostać zatrzymany i nie można go zmienić w jakikolwiek sposób, podczas gdy `ICorDebug*` interfejsy (i w związku z tym `ICorDebugDataTarget` metody) są wywoływane. Jeśli obiektem docelowym jest proces na żywo, a jego stan zmieni się, należy ponownie wywołać metodę [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) w celu zapewnienia zastępczego wystąpienia ICorDebugProcess.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
