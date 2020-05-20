---
title: ISymUnmanagedVariable::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: b48d131fa99b65d38856d2b635bf59145db9157e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615244"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="cb37a-102">ISymUnmanagedVariable::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb37a-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="cb37a-103">Pobiera nazwę tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cb37a-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb37a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb37a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb37a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb37a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cb37a-106">podczas Długość buforu, `pcchName` do którego wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="cb37a-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cb37a-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora, który musi zawierać nazwę, łącznie z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="cb37a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="cb37a-108">określoną Bufor przechowujący nazwę.</span><span class="sxs-lookup"><span data-stu-id="cb37a-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb37a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cb37a-109">Return Value</span></span>  
 <span data-ttu-id="cb37a-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="cb37a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb37a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb37a-111">Requirements</span></span>  
 <span data-ttu-id="cb37a-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cb37a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb37a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb37a-113">See also</span></span>

- [<span data-ttu-id="cb37a-114">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb37a-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
