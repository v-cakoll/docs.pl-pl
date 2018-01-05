---
title: "ICorDebugAssembly::GetCodeBase — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetCodeBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetCodeBase
helpviewer_keywords:
- GetCodeBase method [.NET Framework debugging]
- ICorDebugAssembly::GetCodeBase method [.NET Framework debugging]
ms.assetid: 48adc154-9058-4fef-9c43-e9aad80e4dbf
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24ac81f841be21fe477ad46ef210e2f7d1595acb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetcodebase-method"></a><span data-ttu-id="de35f-102">ICorDebugAssembly::GetCodeBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="de35f-102">ICorDebugAssembly::GetCodeBase Method</span></span>
<span data-ttu-id="de35f-103">Ta metoda nie jest zaimplementowana w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de35f-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de35f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de35f-104">Syntax</span></span>  
  
```  
HRESULT GetCodeBase (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR szName[]  
);  
```
