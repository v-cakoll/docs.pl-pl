---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bac541909e07aadff06006fba8c3cfcf4dc5465
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486228"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="185bb-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="185bb-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="185bb-103">Zdefiniuj grupę async operator await operacji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="185bb-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="185bb-104">Przesunięcie każdego yield pasuje do zwrotu instrukcji await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="185bb-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="185bb-105">Każdy `breakpointMethod` / `breakpointOffset` pary informuje NAS, gdzie operacja asynchroniczna zostanie wznowione, co może być w innej metody.</span><span class="sxs-lookup"><span data-stu-id="185bb-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185bb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="185bb-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="185bb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="185bb-107">Parameters</span></span>  
  
|<span data-ttu-id="185bb-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="185bb-108">Parameter</span></span>|<span data-ttu-id="185bb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="185bb-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="185bb-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="185bb-110">Return Value</span></span>  
 <span data-ttu-id="185bb-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="185bb-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185bb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="185bb-112">Requirements</span></span>  
 <span data-ttu-id="185bb-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="185bb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185bb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="185bb-114">See also</span></span>
- [<span data-ttu-id="185bb-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="185bb-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
