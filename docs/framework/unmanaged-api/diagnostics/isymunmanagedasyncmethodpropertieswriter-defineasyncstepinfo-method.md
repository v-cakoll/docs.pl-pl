---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129196"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="571b4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="571b4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="571b4-103">Zdefiniuj grupę asynchronicznych operacji await w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="571b4-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="571b4-104">Każde przesunięcie Yield pasuje do instrukcji return oczekującej, identyfikując potencjalną rentowność.</span><span class="sxs-lookup"><span data-stu-id="571b4-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="571b4-105">Każda `breakpointMethod`/`breakpointOffset` para informuje nas, gdzie zostanie wznowiona operacja asynchroniczna, która może znajdować się w innej metodzie.</span><span class="sxs-lookup"><span data-stu-id="571b4-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571b4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="571b4-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="571b4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="571b4-107">Parameters</span></span>  
  
|<span data-ttu-id="571b4-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="571b4-108">Parameter</span></span>|<span data-ttu-id="571b4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="571b4-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="571b4-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="571b4-110">Return Value</span></span>  
 <span data-ttu-id="571b4-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="571b4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="571b4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="571b4-112">Requirements</span></span>  
 <span data-ttu-id="571b4-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="571b4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571b4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="571b4-114">See also</span></span>

- [<span data-ttu-id="571b4-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="571b4-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
