---
title: ICLRProbingAssemblyEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: e1e114070f39e75254fc1bc0f8c1bf3e4733d5a2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703373"
---
# <a name="iclrprobingassemblyenum-interface"></a>ICLRProbingAssemblyEnum — Interfejs
Dostarcza metody, które umożliwiają hostowi pobieranie tożsamości dla zestawu przy użyciu informacji o tożsamości zestawu, które są wewnętrzne dla środowiska uruchomieniowego języka wspólnego (CLR), bez konieczności tworzenia lub zrozumienia tożsamości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Get, metoda](iclrprobingassemblyenum-get-method.md)|Pobiera tożsamość zestawu o określonym indeksie.|  
  
## <a name="remarks"></a>Uwagi  
 Metody, takie jak [ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference —](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) , zwracają `ICLRProbingAssemblyEnum` wystąpienie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyIdentityManager, interfejs](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
