---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 05867af48b64cd1898b13fa055859c8cc0367c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949581"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="0059b-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="0059b-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="0059b-103">Wylicza następnego `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktury na liście modułu wyliczającego, zwracając je w `rgelt` wraz z liczbą rzeczywiste elementy wyliczenia `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="0059b-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0059b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0059b-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0059b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0059b-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="0059b-106">[in] Liczba [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) konstrukcje zwracane w `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="0059b-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="0059b-107">[out] Tablica celt rozmiaru (lub większy) do odbierania wyliczany RAWINPUTDEVICE struktury.</span><span class="sxs-lookup"><span data-stu-id="0059b-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="0059b-108">[out] Wskaźnik do liczby elementów, które rzeczywiście zostały podane w `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="0059b-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="0059b-109">Obiekt wywołujący może przekazać w `NULL` Jeśli `rgelt` jeden.</span><span class="sxs-lookup"><span data-stu-id="0059b-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0059b-110">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="0059b-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="0059b-111">HRESULT: S_OK, jeśli liczba elementów, które podano `celt`; W przeciwnym razie S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="0059b-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
