---
title: ICorProfilerCallback::ModuleAttachedToAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 791827b9c4b60cb2ee963881bc8e1a6131cd00fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139922"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly — Metoda
Powiadamia program profilujący, że moduł jest dołączany do własnego zestawu nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, który jest dołączony.  
  
 `AssemblyId`  
 [in] Identyfikator zestawu nadrzędnego, do której jest dołączony modułu.  
  
## <a name="remarks"></a>Uwagi  
 Moduł może zostać załadowany przy użyciu tabeli adresów importowania (IAT) za pomocą wywołania `LoadLibrary`, lub za pomocą odwołania metadanych. W wyniku wspólnej ładujący środowisko uruchomieniowe (języka wspólnego CLR) języka ma wiele ścieżek kodu do określania zestawu, w którym są przechowywane w module. W związku z tym, istnieje możliwość, że po [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) jest wywoływana, moduł nie wie, jakiego zestawu znajduje się w i uzyskiwanie Identyfikatora zestawu nadrzędnego nie jest możliwe. `ModuleAttachedToAssembly` Metoda jest wywoływana, gdy moduł jest dołączony do zestawu nadrzędnej i jej zestawu nadrzędny można uzyskać Identyfikatora.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
