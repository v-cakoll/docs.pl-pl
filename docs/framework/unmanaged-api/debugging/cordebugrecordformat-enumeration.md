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
ms.openlocfilehash: a27c96a7be9b5d868e07da11f1a239b9dd5fe2f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="c7277-102">Wyliczenie CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="c7277-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="c7277-103">Opisuje format danych w tablicy bajtów, który zawiera informacje dotyczące zdarzenia debugowania natywnego wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c7277-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7277-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7277-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="c7277-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c7277-105">Members</span></span>  
  
|<span data-ttu-id="c7277-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c7277-106">Member</span></span>|<span data-ttu-id="c7277-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c7277-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="c7277-108">Dane są rekord wyjątek 32-bitowego systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c7277-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="c7277-109">Dane są rekord wyjątek 64-bitowego systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c7277-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7277-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7277-110">Remarks</span></span>  
 <span data-ttu-id="c7277-111">Członek `CorDebugRecordFormat` wyliczenie jest przekazywana do [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody, aby wskazać format tablicy bajtów w jego `pRecord` argumentu.</span><span class="sxs-lookup"><span data-stu-id="c7277-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7277-112">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="c7277-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7277-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7277-113">Requirements</span></span>  
 <span data-ttu-id="c7277-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7277-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7277-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7277-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7277-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7277-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7277-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7277-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7277-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7277-118">See Also</span></span>  
 [<span data-ttu-id="c7277-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c7277-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
