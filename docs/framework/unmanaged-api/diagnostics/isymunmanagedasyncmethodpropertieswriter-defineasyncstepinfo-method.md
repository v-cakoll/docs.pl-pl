---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b165501b3e090cf309f3b4053649644b87b47f22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555573"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="eb792-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb792-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="eb792-103">Zdefiniuj grupę async operator await operacji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="eb792-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="eb792-104">Przesunięcie każdego yield pasuje do zwrotu instrukcji await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="eb792-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="eb792-105">Każdy `breakpointMethod` / `breakpointOffset` pary informuje NAS, gdy operacja asynchroniczna zostanie wznowiona, (która może być w innej metody.</span><span class="sxs-lookup"><span data-stu-id="eb792-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb792-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb792-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb792-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb792-107">Parameters</span></span>  
  
|<span data-ttu-id="eb792-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="eb792-108">Parameter</span></span>|<span data-ttu-id="eb792-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eb792-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="eb792-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb792-110">Return Value</span></span>  
 <span data-ttu-id="eb792-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="eb792-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb792-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb792-112">Requirements</span></span>  
 <span data-ttu-id="eb792-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eb792-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb792-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb792-114">See also</span></span>
- [<span data-ttu-id="eb792-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb792-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
