---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: ccf1287a1b0218e7f2560e1afbb0930c93b43263
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129171"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="1c0ac-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c0ac-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="1c0ac-103">Ustawia metodę początkową inicjującą operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c0ac-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c0ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c0ac-105">Parameters</span></span>  
  
|<span data-ttu-id="1c0ac-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="1c0ac-106">Parameter</span></span>|<span data-ttu-id="1c0ac-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1c0ac-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="1c0ac-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c0ac-108">Return Value</span></span>  
 <span data-ttu-id="1c0ac-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c0ac-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c0ac-110">Requirements</span></span>  
 <span data-ttu-id="1c0ac-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1c0ac-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0ac-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c0ac-112">See also</span></span>

- [<span data-ttu-id="1c0ac-113">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c0ac-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
