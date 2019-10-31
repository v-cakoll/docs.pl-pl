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
ms.openlocfilehash: 80979f0424469bb1d4771ad6507bb8c9d5364ab4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108608"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="afbf2-102">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="afbf2-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="afbf2-103">Tworzy czytelnika historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="afbf2-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afbf2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afbf2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="afbf2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afbf2-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="afbf2-106">podczas Ścieżka pliku.</span><span class="sxs-lookup"><span data-stu-id="afbf2-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="afbf2-107">określoną Po pomyślnym zakończeniu zawiera wskaźnik do czytnika historii.</span><span class="sxs-lookup"><span data-stu-id="afbf2-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afbf2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="afbf2-108">Return Value</span></span>  
 <span data-ttu-id="afbf2-109">Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz wartości opisanych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="afbf2-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="afbf2-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="afbf2-110">Return code</span></span>|<span data-ttu-id="afbf2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="afbf2-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="afbf2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="afbf2-112">S_OK</span></span>|<span data-ttu-id="afbf2-113">Wskazuje, że metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="afbf2-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="afbf2-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="afbf2-114">E_INVALIDARG</span></span>|<span data-ttu-id="afbf2-115">Wskazuje, że `wzFilePath` lub `ppHistoryReader` są ustawione na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="afbf2-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="afbf2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afbf2-116">Requirements</span></span>  
 <span data-ttu-id="afbf2-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afbf2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afbf2-118">**Biblioteka:** Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="afbf2-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="afbf2-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afbf2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbf2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afbf2-120">See also</span></span>

- [<span data-ttu-id="afbf2-121">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="afbf2-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
