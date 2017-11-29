---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e305ca13e419a40e9838a46a61fe7a435b7ce56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="2df2e-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="2df2e-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="2df2e-103">Zdefiniuj grupę asynchronicznych operacji w bieżącej metodzie await.</span><span class="sxs-lookup"><span data-stu-id="2df2e-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="2df2e-104">Przesunięcie każdego yield odpowiada instrukcji return await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="2df2e-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="2df2e-105">Każdy `breakpointMethod` / `breakpointOffset` pary informuje, nam gdzie operację asynchroniczną zostanie wznowiona, (która może być w innej metody.</span><span class="sxs-lookup"><span data-stu-id="2df2e-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df2e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2df2e-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2df2e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2df2e-107">Parameters</span></span>  
  
|<span data-ttu-id="2df2e-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="2df2e-108">Parameter</span></span>|<span data-ttu-id="2df2e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2df2e-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="2df2e-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2df2e-110">Return Value</span></span>  
 <span data-ttu-id="2df2e-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2df2e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df2e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2df2e-112">Requirements</span></span>  
 <span data-ttu-id="2df2e-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2df2e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df2e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2df2e-114">See Also</span></span>  
 [<span data-ttu-id="2df2e-115">Isymunmanagedasyncmethodpropertieswriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="2df2e-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
