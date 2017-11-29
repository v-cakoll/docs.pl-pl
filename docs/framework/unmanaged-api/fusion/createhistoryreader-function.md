---
title: "CreateHistoryReader — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateHistoryReader
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateHistoryReader
helpviewer_keywords: CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f4b09f592a27b7d3d25b2dbe13be7e261023bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="316c5-102">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="316c5-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="316c5-103">Tworzy czytnik historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="316c5-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="316c5-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="316c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="316c5-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="316c5-106">[in] Ścieżka do pliku.</span><span class="sxs-lookup"><span data-stu-id="316c5-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="316c5-107">[out] Po pomyślnym ukończeniu zawiera wskaźnik do czytnika historii.</span><span class="sxs-lookup"><span data-stu-id="316c5-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="316c5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="316c5-108">Return Value</span></span>  
 <span data-ttu-id="316c5-109">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h, oprócz wartości opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="316c5-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="316c5-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="316c5-110">Return code</span></span>|<span data-ttu-id="316c5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="316c5-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="316c5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="316c5-112">S_OK</span></span>|<span data-ttu-id="316c5-113">Wskazuje, czy metoda zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="316c5-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="316c5-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="316c5-114">E_INVALIDARG</span></span>|<span data-ttu-id="316c5-115">Oznacza to, że `wzFilePath` lub `ppHistoryReader` są ustawione na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="316c5-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="316c5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="316c5-116">Requirements</span></span>  
 <span data-ttu-id="316c5-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="316c5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="316c5-118">**Biblioteka:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="316c5-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="316c5-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="316c5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316c5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="316c5-120">See Also</span></span>  
 [<span data-ttu-id="316c5-121">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="316c5-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
