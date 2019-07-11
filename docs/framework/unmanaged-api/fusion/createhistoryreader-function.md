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
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778416"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="f360a-102">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f360a-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="f360a-103">Tworzy czytnik historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="f360a-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f360a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f360a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f360a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f360a-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="f360a-106">[in] Ścieżka do pliku.</span><span class="sxs-lookup"><span data-stu-id="f360a-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="f360a-107">[out] Po pomyślnym zakończeniu zawiera wskaźnik do czytnika historii.</span><span class="sxs-lookup"><span data-stu-id="f360a-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f360a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f360a-108">Return Value</span></span>  
 <span data-ttu-id="f360a-109">Ta metoda zwraca standardowych kodów błędu modelu COM, zgodnie z definicją w pliku WinError.h, oprócz wartości opisanych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f360a-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="f360a-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="f360a-110">Return code</span></span>|<span data-ttu-id="f360a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f360a-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f360a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f360a-112">S_OK</span></span>|<span data-ttu-id="f360a-113">Wskazuje, czy metoda zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f360a-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="f360a-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f360a-114">E_INVALIDARG</span></span>|<span data-ttu-id="f360a-115">Oznacza to, że `wzFilePath` lub `ppHistoryReader` są ustawione na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f360a-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f360a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f360a-116">Requirements</span></span>  
 <span data-ttu-id="f360a-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f360a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f360a-118">**Biblioteka:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="f360a-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="f360a-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f360a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f360a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f360a-120">See also</span></span>

- [<span data-ttu-id="f360a-121">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f360a-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
