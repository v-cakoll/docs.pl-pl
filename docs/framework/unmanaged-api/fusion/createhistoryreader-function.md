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
ms.openlocfilehash: 2710d14d6e73879fd17a6b58659463ea205f2384
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795366"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="13ca5-102">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="13ca5-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="13ca5-103">Tworzy czytelnika historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="13ca5-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ca5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13ca5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="13ca5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13ca5-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="13ca5-106">podczas Ścieżka pliku.</span><span class="sxs-lookup"><span data-stu-id="13ca5-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="13ca5-107">określoną Po pomyślnym zakończeniu zawiera wskaźnik do czytnika historii.</span><span class="sxs-lookup"><span data-stu-id="13ca5-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13ca5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13ca5-108">Return Value</span></span>  
 <span data-ttu-id="13ca5-109">Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz wartości opisanych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="13ca5-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="13ca5-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="13ca5-110">Return code</span></span>|<span data-ttu-id="13ca5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="13ca5-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="13ca5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="13ca5-112">S_OK</span></span>|<span data-ttu-id="13ca5-113">Wskazuje, że metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="13ca5-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="13ca5-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="13ca5-114">E_INVALIDARG</span></span>|<span data-ttu-id="13ca5-115">Wskazuje, `wzFilePath` że `ppHistoryReader` lub są ustawione na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="13ca5-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13ca5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13ca5-116">Requirements</span></span>  
 <span data-ttu-id="13ca5-117">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13ca5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13ca5-118">**Biblioteki** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="13ca5-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="13ca5-119">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13ca5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ca5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13ca5-120">See also</span></span>

- [<span data-ttu-id="13ca5-121">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="13ca5-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
