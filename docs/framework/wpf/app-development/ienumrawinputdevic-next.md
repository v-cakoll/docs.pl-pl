---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 329a2cd96346e199ee834856dd6dbfac6175b722
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515320"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="5e013-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="5e013-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="5e013-103">Wylicza następnego `celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury na liście modułu wyliczającego, zwracając je w `rgelt` wraz z liczbą rzeczywiste elementy wyliczenia `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="5e013-103">Enumerates the next `celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e013-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e013-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e013-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e013-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="5e013-106">[in] Liczba [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) konstrukcje zwracane w `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="5e013-106">[in] Number of [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="5e013-107">[out] Tablica celt rozmiaru (lub większy) do odbierania wyliczany RAWINPUTDEVICE struktury.</span><span class="sxs-lookup"><span data-stu-id="5e013-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="5e013-108">[out] Wskaźnik do liczby elementów, które rzeczywiście zostały podane w `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="5e013-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="5e013-109">Obiekt wywołujący może przekazać w `NULL` Jeśli `rgelt` jeden.</span><span class="sxs-lookup"><span data-stu-id="5e013-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5e013-110">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="5e013-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="5e013-111">HRESULT: S_OK, jeśli liczba elementów, które podano `celt`; W przeciwnym razie S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="5e013-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
