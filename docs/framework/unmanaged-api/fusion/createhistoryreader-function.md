---
title: CreateHistoryReader — Funkcja
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e438006d6424866514e73119c05e8fd69d7ba62e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669709"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="f37d2-102">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f37d2-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="f37d2-103">Tworzy czytnik historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="f37d2-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f37d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f37d2-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f37d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f37d2-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="f37d2-106">[in] Ścieżka do pliku.</span><span class="sxs-lookup"><span data-stu-id="f37d2-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="f37d2-107">[out] Po pomyślnym zakończeniu zawiera wskaźnik do czytnika historii.</span><span class="sxs-lookup"><span data-stu-id="f37d2-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f37d2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f37d2-108">Return Value</span></span>  
 <span data-ttu-id="f37d2-109">Ta metoda zwraca standardowych kodów błędu modelu COM, zgodnie z definicją w pliku WinError.h, oprócz wartości opisanych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f37d2-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="f37d2-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="f37d2-110">Return code</span></span>|<span data-ttu-id="f37d2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f37d2-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f37d2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f37d2-112">S_OK</span></span>|<span data-ttu-id="f37d2-113">Wskazuje, czy metoda zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f37d2-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="f37d2-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f37d2-114">E_INVALIDARG</span></span>|<span data-ttu-id="f37d2-115">Oznacza to, że `wzFilePath` lub `ppHistoryReader` są ustawione na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f37d2-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f37d2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f37d2-116">Requirements</span></span>  
 <span data-ttu-id="f37d2-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f37d2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f37d2-118">**Biblioteka:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="f37d2-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="f37d2-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f37d2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37d2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f37d2-120">See also</span></span>

- [<span data-ttu-id="f37d2-121">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f37d2-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
