---
title: ICorPublish::EnumProcesses — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f785b22a3fbda6403c124ec70757b16f5335907
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790769"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="06297-102">ICorPublish::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="06297-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="06297-103">Pobiera moduł wyliczający dla zarządzanych procesów uruchomionych na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="06297-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06297-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06297-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06297-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06297-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="06297-106">Wartość wyliczenia [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) , która określa typ procesu do pobrania.</span><span class="sxs-lookup"><span data-stu-id="06297-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="06297-107">W bieżącej wersji tylko COR_PUB_MANAGEDONLY jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="06297-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="06297-108">Wskaźnik do adresu wystąpienia [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) , który jest modułem wyliczającym procesy.</span><span class="sxs-lookup"><span data-stu-id="06297-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06297-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06297-109">Remarks</span></span>  
 <span data-ttu-id="06297-110">Kolekcja procesów modułu wyliczającego jest oparta na migawce procesów, które są uruchomione, gdy wywoływana jest metoda `EnumProcesses`.</span><span class="sxs-lookup"><span data-stu-id="06297-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="06297-111">Moduł wyliczający nie będzie zawierać żadnych procesów kończących się przed lub po wywołaniu `EnumProcesses`.</span><span class="sxs-lookup"><span data-stu-id="06297-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="06297-112">Metoda `EnumProcesses` może być wywoływana więcej niż raz w tym wystąpieniu [ICorPublish](icorpublish-interface.md) , aby utworzyć nową, aktualną kolekcję procesów.</span><span class="sxs-lookup"><span data-stu-id="06297-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="06297-113">Kolejne wywołania metody `EnumProcesses` nie będą miały wpływ na istniejące kolekcje.</span><span class="sxs-lookup"><span data-stu-id="06297-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06297-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06297-114">Requirements</span></span>  
 <span data-ttu-id="06297-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06297-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06297-116">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="06297-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="06297-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06297-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06297-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06297-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06297-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06297-119">See also</span></span>

- [<span data-ttu-id="06297-120">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="06297-120">ICorPublish Interface</span></span>](icorpublish-interface.md)
