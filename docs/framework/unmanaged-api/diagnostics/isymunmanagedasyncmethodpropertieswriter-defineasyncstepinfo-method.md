---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8305d0a562fd90e3fae32e372b663ca3942d2a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940143"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="75510-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="75510-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="75510-103">Zdefiniuj grupę async operator await operacji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="75510-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="75510-104">Przesunięcie każdego yield pasuje do zwrotu instrukcji await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="75510-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="75510-105">Każdy `breakpointMethod` / `breakpointOffset` pary informuje NAS, gdzie operacja asynchroniczna zostanie wznowione, co może być w innej metody.</span><span class="sxs-lookup"><span data-stu-id="75510-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75510-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="75510-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75510-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="75510-107">Parameters</span></span>  
  
|<span data-ttu-id="75510-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="75510-108">Parameter</span></span>|<span data-ttu-id="75510-109">Opis</span><span class="sxs-lookup"><span data-stu-id="75510-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="75510-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75510-110">Return Value</span></span>  
 <span data-ttu-id="75510-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="75510-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75510-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75510-112">Requirements</span></span>  
 <span data-ttu-id="75510-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="75510-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75510-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75510-114">See also</span></span>

- [<span data-ttu-id="75510-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="75510-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
