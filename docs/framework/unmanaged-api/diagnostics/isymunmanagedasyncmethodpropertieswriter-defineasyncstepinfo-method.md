---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebd4bb1d674a27785ccbe5460a65fed764638ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435880"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="effce-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="effce-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="effce-103">Zdefiniuj grupę asynchronicznych operacji w bieżącej metodzie await.</span><span class="sxs-lookup"><span data-stu-id="effce-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="effce-104">Przesunięcie każdego yield odpowiada instrukcji return await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="effce-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="effce-105">Każdy `breakpointMethod` / `breakpointOffset` pary informuje, nam gdzie operację asynchroniczną zostanie wznowiona, (która może być w innej metody.</span><span class="sxs-lookup"><span data-stu-id="effce-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effce-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="effce-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="effce-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="effce-107">Parameters</span></span>  
  
|<span data-ttu-id="effce-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="effce-108">Parameter</span></span>|<span data-ttu-id="effce-109">Opis</span><span class="sxs-lookup"><span data-stu-id="effce-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="effce-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="effce-110">Return Value</span></span>  
 <span data-ttu-id="effce-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="effce-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="effce-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="effce-112">Requirements</span></span>  
 <span data-ttu-id="effce-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="effce-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effce-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="effce-114">See Also</span></span>  
 [<span data-ttu-id="effce-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="effce-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
