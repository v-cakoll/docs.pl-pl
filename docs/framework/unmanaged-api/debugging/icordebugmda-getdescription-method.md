---
title: ICorDebugMDA::GetDescription — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: 522e992e6d7e9a64f7590bbec0e9106e0e1f8f47
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212142"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="fbb0e-102">ICorDebugMDA::GetDescription — Metoda</span><span class="sxs-lookup"><span data-stu-id="fbb0e-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="fbb0e-103">Pobiera ciąg zawierający opis zarządzanego asystenta debugowania (MDA) reprezentowanego przez [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fbb0e-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb0e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbb0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbb0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbb0e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="fbb0e-106">podczas Rozmiar buforu ciągu, który będzie przechowywać opis.</span><span class="sxs-lookup"><span data-stu-id="fbb0e-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fbb0e-107">określoną Wskaźnik do liczby bajtów zwróconych w buforze ciągów.</span><span class="sxs-lookup"><span data-stu-id="fbb0e-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="fbb0e-108">określoną Bufor ciągu zawierający opis MDA.</span><span class="sxs-lookup"><span data-stu-id="fbb0e-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb0e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbb0e-109">Remarks</span></span>  
 <span data-ttu-id="fbb0e-110">Ciąg może mieć długość zero.</span><span class="sxs-lookup"><span data-stu-id="fbb0e-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb0e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbb0e-111">Requirements</span></span>  
 <span data-ttu-id="fbb0e-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb0e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb0e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fbb0e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbb0e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fbb0e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb0e-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb0e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb0e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbb0e-116">See also</span></span>

- [<span data-ttu-id="fbb0e-117">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fbb0e-117">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="fbb0e-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="fbb0e-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
