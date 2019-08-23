---
title: Wyliczenie CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6ed7d25593f9dd5d5d01f8c06024dcf8acfcfea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916473"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="cbd5a-102">Wyliczenie CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="cbd5a-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="cbd5a-103">Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cbd5a-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbd5a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="cbd5a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cbd5a-105">Members</span></span>  
  
|<span data-ttu-id="cbd5a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cbd5a-106">Member</span></span>|<span data-ttu-id="cbd5a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cbd5a-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="cbd5a-108">Dane to 32-bitowy rekord wyjątku systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cbd5a-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="cbd5a-109">Dane to 64-bitowy rekord wyjątku systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cbd5a-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbd5a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbd5a-110">Remarks</span></span>  
 <span data-ttu-id="cbd5a-111">Element członkowski `CorDebugRecordFormat` wyliczenia jest przesyłany do metody [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) w celu wskazania formatu tablicy `pRecord` bajtów w argumencie.</span><span class="sxs-lookup"><span data-stu-id="cbd5a-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbd5a-112">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cbd5a-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd5a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbd5a-113">Requirements</span></span>  
 <span data-ttu-id="cbd5a-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd5a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd5a-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbd5a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbd5a-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbd5a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbd5a-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd5a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd5a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbd5a-118">See also</span></span>

- [<span data-ttu-id="cbd5a-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="cbd5a-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
