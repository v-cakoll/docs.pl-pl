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
ms.openlocfilehash: 0a433ccb81ef62ac92a4553a838a2c98a04fc7c1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212818"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="a93bc-102">ICorDebugProcess::WriteMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="a93bc-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="a93bc-103">Zapisuje dane w obszarze pamięci w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="a93bc-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a93bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a93bc-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a93bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a93bc-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="a93bc-106">podczas `CORDB_ADDRESS`Wartość, która jest adresem podstawowym obszaru pamięci, do którego zapisywane są dane.</span><span class="sxs-lookup"><span data-stu-id="a93bc-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="a93bc-107">Przed przeprowadzeniem transferu danych system weryfikuje, czy obszar pamięci o określonym rozmiarze, zaczynając od adresu podstawowego, jest dostępny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="a93bc-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="a93bc-108">Jeśli nie jest dostępny, Metoda kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a93bc-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="a93bc-109">podczas Liczba bajtów do zapisania w obszarze pamięci.</span><span class="sxs-lookup"><span data-stu-id="a93bc-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a93bc-110">podczas Bufor zawierający dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="a93bc-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="a93bc-111">określoną Wskaźnik do zmiennej, która odbiera liczbę bajtów zapisywanych w obszarze pamięci w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="a93bc-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="a93bc-112">Jeśli `written` ma wartość null, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="a93bc-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a93bc-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a93bc-113">Remarks</span></span>  
 <span data-ttu-id="a93bc-114">Dane są automatycznie zapisywane za dowolnymi punktami przerwania.</span><span class="sxs-lookup"><span data-stu-id="a93bc-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="a93bc-115">W .NET Framework w wersji 2,0 debugery natywne nie powinny używać tej metody do dodawania punktów przerwania do strumienia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a93bc-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="a93bc-116">Zamiast tego użyj [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a93bc-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="a93bc-117">`WriteMemory`Metoda powinna być używana tylko poza kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="a93bc-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="a93bc-118">Ta metoda może uszkodzić środowisko uruchomieniowe, jeśli jest używane nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a93bc-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a93bc-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a93bc-119">Requirements</span></span>  
 <span data-ttu-id="a93bc-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a93bc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a93bc-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a93bc-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a93bc-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a93bc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a93bc-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a93bc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
