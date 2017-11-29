---
title: "ICorProfilerInfo::GetILFunctionBody — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6908b6c765a56ef0aa43a66cc58ec74b525bc2d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody — Metoda
Pobiera wskaźnik do treści metody w kodzie języka pośredniego (MSIL) firmy Microsoft, zaczynając od jej nagłówek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, w której znajduje się funkcja.  
  
 `methodId`  
 [in] Token metadanych dla metody.  
  
 `ppMethodHeader`  
 [out] Wskaźnik do nagłówka metody.  
  
 `pcbMethodSize`  
 [out] Liczba całkowita określająca rozmiar metody.  
  
## <a name="remarks"></a>Uwagi  
 Metoda ma zakres przez moduł, w którym mieszka. Ponieważ `GetILFunctionBody` metoda jest przeznaczona do udostępnienia narzędzie kod MSIL przed został załadowany przez środowisko uruchomieniowe języka wspólnego (CLR), używa token metadanych metody, aby znaleźć odpowiednie wystąpienie.  
  
 `GetILFunctionBody`może zwrócić CORPROF_E_FUNCTION_NOT_IL HRESULT, jeśli `methodId` wskazuje metodę bez żadnych MSIL kodu (takie jak metoda abstrakcyjna lub platformę invoke — metoda (funkcja PInvoke)).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
