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
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133930"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager — Interfejs
Definiuje metody, które pozwalają hostowi uzyskać informacje o żądanych zadaniach i wykryć zakleszczenie w swojej implementacji synchronizacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator, metoda](iclrsyncmanager-createrwlockowneriterator-method.md)|Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) tworzy iterator dla hosta do użycia w celu określenia zestawu zadań oczekujących na blokadę modułu odczytującego.|  
|[DeleteRWLockOwnerIterator, metoda](iclrsyncmanager-deleterwlockowneriterator-method.md)|Żądania, aby środowisko CLR zniszczyć iterator, który został utworzony przez wywołanie do `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner, metoda](iclrsyncmanager-getmonitorowner-method.md)|Pobiera zadanie, które jest właścicielem określonego monitora.|  
|[GetRWLockOwnerNext, metoda](iclrsyncmanager-getrwlockownernext-method.md)|Pobiera następne zadanie czekające na bieżącą blokadę modułu odczytującego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
- [Wątki zarządzane i niezarządzane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Hosting, interfejsy](hosting-interfaces.md)
