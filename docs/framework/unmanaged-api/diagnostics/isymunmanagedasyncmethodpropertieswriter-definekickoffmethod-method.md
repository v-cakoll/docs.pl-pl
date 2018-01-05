---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 691a46e20339b659b5df3136d4dca6c03a69d3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="516c4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="516c4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="516c4-103">Ustawia metodę początkową, który inicjuje operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="516c4-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="516c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="516c4-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="516c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="516c4-105">Parameters</span></span>  
  
|<span data-ttu-id="516c4-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="516c4-106">Parameter</span></span>|<span data-ttu-id="516c4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="516c4-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="516c4-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="516c4-108">Return Value</span></span>  
 <span data-ttu-id="516c4-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="516c4-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="516c4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="516c4-110">Requirements</span></span>  
 <span data-ttu-id="516c4-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="516c4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516c4-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="516c4-112">See Also</span></span>  
 [<span data-ttu-id="516c4-113">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="516c4-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
