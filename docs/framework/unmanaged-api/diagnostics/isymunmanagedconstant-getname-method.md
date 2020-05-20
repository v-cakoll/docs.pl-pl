---
title: ISymUnmanagedConstant::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441646"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="77803-102">ISymUnmanagedConstant::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="77803-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="77803-103">Pobiera nazwę stałej.</span><span class="sxs-lookup"><span data-stu-id="77803-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77803-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77803-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77803-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77803-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="77803-106">podczas Długość buforu, `szName` do którego wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="77803-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="77803-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora, który musi zawierać nazwę, łącznie z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="77803-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="77803-108">określoną Bufor przechowujący nazwę.</span><span class="sxs-lookup"><span data-stu-id="77803-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77803-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77803-109">Return Value</span></span>  
 <span data-ttu-id="77803-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="77803-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77803-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77803-111">Requirements</span></span>  
 <span data-ttu-id="77803-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="77803-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77803-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77803-113">See also</span></span>

- [<span data-ttu-id="77803-114">ISymUnmanagedConstant — Interfejs</span><span class="sxs-lookup"><span data-stu-id="77803-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="77803-115">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="77803-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="77803-116">GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="77803-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
