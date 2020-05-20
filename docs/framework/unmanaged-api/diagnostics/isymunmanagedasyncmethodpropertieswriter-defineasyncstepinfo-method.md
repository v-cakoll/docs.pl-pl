---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 5a501cca16f06e7ccd5da9f65a213c6b24c1092c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441789"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="d3ee9-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3ee9-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="d3ee9-103">Zdefiniuj grupę asynchronicznych operacji await w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="d3ee9-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="d3ee9-104">Każde przesunięcie Yield pasuje do instrukcji return oczekującej, identyfikując potencjalną rentowność.</span><span class="sxs-lookup"><span data-stu-id="d3ee9-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="d3ee9-105">Każda `breakpointMethod` / `breakpointOffset` para informuje nas, gdzie zostanie wznowiona operacja asynchroniczna, która może znajdować się w innej metodzie.</span><span class="sxs-lookup"><span data-stu-id="d3ee9-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ee9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3ee9-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3ee9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3ee9-107">Parameters</span></span>  
  
|<span data-ttu-id="d3ee9-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="d3ee9-108">Parameter</span></span>|<span data-ttu-id="d3ee9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d3ee9-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="d3ee9-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3ee9-110">Return Value</span></span>  
 <span data-ttu-id="d3ee9-111">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d3ee9-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3ee9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3ee9-112">Requirements</span></span>  
 <span data-ttu-id="d3ee9-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d3ee9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ee9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3ee9-114">See also</span></span>

- [<span data-ttu-id="d3ee9-115">ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3ee9-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
