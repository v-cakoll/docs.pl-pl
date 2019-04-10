---
title: ICorProfilerInfo::GetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2960bc0cfc39adb9b7cbca236d495baf630a173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201419"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody — Metoda
Pobiera wskaźnik do treści metody w kodzie języka intermediate language (MSIL) firmy Microsoft, zaczynając od jej nagłówek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, w której znajduje się funkcja.  
  
 `methodId`  
 [in] Token metadanych dla metody.  
  
 `ppMethodHeader`  
 [out] Wskaźnik do nagłówka metody.  
  
 `pcbMethodSize`  
 [out] Liczba całkowita określająca rozmiar metody.  
  
## <a name="remarks"></a>Uwagi  
 Metoda obejmuje przez moduł, w którym się znajdują. Ponieważ `GetILFunctionBody` metoda kwotę ustalono, aby udzielić dostępu narzędzie do kodu MSIL, zanim został załadowany przez środowisko uruchomieniowe języka wspólnego (CLR), używa tokenu metadanych, metody można znaleźć żądanego wystąpienia.  
  
 `GetILFunctionBody` może zwracać CORPROF_E_FUNCTION_NOT_IL HRESULT, jeśli `methodId` wskazuje metodę bez żadnych MSIL kod (takie jak metody abstrakcyjnej lub platformę invoke, metoda (funkcja PInvoke)).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
