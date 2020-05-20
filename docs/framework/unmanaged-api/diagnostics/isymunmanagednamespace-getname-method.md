---
title: ISymUnmanagedNamespace::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 84b2f1226c84713483499c7ff777838058cb0f95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615114"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="9a7ae-102">ISymUnmanagedNamespace::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a7ae-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="9a7ae-103">Pobiera nazwę tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9a7ae-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a7ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a7ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a7ae-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9a7ae-106">podczas `ULONG32`Wskazuje rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="9a7ae-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9a7ae-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora, który musi zawierać nazwę przestrzeni nazw, łącznie z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="9a7ae-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a7ae-108">określoną Wskaźnik do buforu, który zawiera nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9a7ae-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a7ae-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9a7ae-109">Return Value</span></span>  
 <span data-ttu-id="9a7ae-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9a7ae-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7ae-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a7ae-111">Requirements</span></span>  
 <span data-ttu-id="9a7ae-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9a7ae-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7ae-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a7ae-113">See also</span></span>

- [<span data-ttu-id="9a7ae-114">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7ae-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
