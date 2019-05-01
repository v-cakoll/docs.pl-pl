---
title: ICorProfilerInfo::ForceGC — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5672d1b89b4260d1ebfbf444deb2702f215a0e95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049651"
---
# <a name="icorprofilerinfoforcegc-method"></a>ICorProfilerInfo::ForceGC — Metoda
Wymusza wyrzucanie elementów bezużytecznych w środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a>Uwagi  
 `ForceGC` Metoda musi zostać wywołana tylko z wątku, który nigdy nie uruchomił kodu zarządzanego, a nie ma żadnych wywołania zwrotne profilera na swój stos. Najwygodniej wdrożenia jest utworzenie oddzielnego wątku w ramach programu profilującego, który wywołuje `ForceGC` podczas zasygnalizowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
