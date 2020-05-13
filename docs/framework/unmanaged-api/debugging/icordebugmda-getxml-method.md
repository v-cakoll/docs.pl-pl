---
title: ICorDebugMDA::GetXML — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207653"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="f5284-102">ICorDebugMDA::GetXML — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5284-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="f5284-103">Pobiera pełny strumień XML skojarzony z zarządzanym asystentem debugowania (MDA) reprezentowany przez [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f5284-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5284-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5284-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5284-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5284-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f5284-106">podczas Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f5284-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f5284-107">określoną Wskaźnik do długości strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="f5284-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="f5284-108">określoną Tablica, w której ma być przechowywany strumień XML.</span><span class="sxs-lookup"><span data-stu-id="f5284-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="f5284-109">Tablica może być pusta.</span><span class="sxs-lookup"><span data-stu-id="f5284-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5284-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5284-110">Remarks</span></span>  
 <span data-ttu-id="f5284-111">`GetXML`Metoda może potencjalnie wpłynąć na wydajność, w zależności od rozmiaru skojarzonego strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="f5284-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5284-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5284-112">Requirements</span></span>  
 <span data-ttu-id="f5284-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5284-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5284-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5284-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5284-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5284-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5284-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5284-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5284-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5284-117">See also</span></span>

- [<span data-ttu-id="f5284-118">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5284-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="f5284-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f5284-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
