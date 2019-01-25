---
title: ICLRSyncManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b949466c5557415ec06bac601380675beed7fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549866"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager — Interfejs
Definiuje metody, które umożliwiają hosta, aby uzyskać informacje o żądanych zadań i wykrył zakleszczenie w jego implementacja synchronizacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator, metoda](iclrsyncmanager-createrwlockowneriterator-method.md)|Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) Utwórz iterator dla hosta na potrzeby określania zestawu zadań, oczekiwania na blokadę zapisu czytnika.|  
|[DeleteRWLockOwnerIterator, metoda](iclrsyncmanager-deleterwlockowneriterator-method.md)|Żądania, że środowisko CLR zniszczyć iterator, który został utworzony przez wywołanie `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner, metoda](iclrsyncmanager-getmonitorowner-method.md)|Pobiera zadanie, które jest właścicielem określony monitor.|  
|[GetRWLockOwnerNext, metoda](iclrsyncmanager-getrwlockownernext-method.md)|Pobiera następne zadanie, które oczekuje na bieżącego czytnika blokadę.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Threading.Thread>
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
- [Zarządzana i niezarządzana wątkowość](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Hosting, interfejsy](hosting-interfaces.md)
