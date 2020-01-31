---
title: ICorDebugProcess::WriteMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: fb3e0ccb57cf3b056bd25e643706e49b8bc75531
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792540"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="de798-102">ICorDebugProcess::WriteMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="de798-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="de798-103">Zapisuje dane w obszarze pamięci w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="de798-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de798-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de798-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de798-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de798-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="de798-106">podczas Wartość `CORDB_ADDRESS`, która jest adresem podstawowym obszaru pamięci, do którego zapisano dane.</span><span class="sxs-lookup"><span data-stu-id="de798-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="de798-107">Przed przeprowadzeniem transferu danych system weryfikuje, czy obszar pamięci o określonym rozmiarze, zaczynając od adresu podstawowego, jest dostępny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="de798-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="de798-108">Jeśli nie jest dostępny, Metoda kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="de798-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="de798-109">podczas Liczba bajtów do zapisania w obszarze pamięci.</span><span class="sxs-lookup"><span data-stu-id="de798-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="de798-110">podczas Bufor zawierający dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="de798-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="de798-111">określoną Wskaźnik do zmiennej, która odbiera liczbę bajtów zapisywanych w obszarze pamięci w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="de798-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="de798-112">Jeśli `written` ma wartość NULL, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="de798-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de798-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de798-113">Remarks</span></span>  
 <span data-ttu-id="de798-114">Dane są automatycznie zapisywane za dowolnymi punktami przerwania.</span><span class="sxs-lookup"><span data-stu-id="de798-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="de798-115">W .NET Framework w wersji 2,0 debugery natywne nie powinny używać tej metody do dodawania punktów przerwania do strumienia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="de798-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="de798-116">Zamiast tego użyj [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de798-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="de798-117">Metoda `WriteMemory` powinna być używana tylko poza kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="de798-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="de798-118">Ta metoda może uszkodzić środowisko uruchomieniowe, jeśli jest używane nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="de798-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de798-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de798-119">Requirements</span></span>  
 <span data-ttu-id="de798-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de798-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de798-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="de798-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de798-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="de798-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de798-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de798-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
