---
title: ICorProfilerInfo3::GetThreadStaticAddress2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: 5ebd1f2780ab25e01bcb384b38220f414d90292e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868541"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="419e6-102">ICorProfilerInfo3::GetThreadStaticAddress2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="419e6-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="419e6-103">Pobiera adres określonego wątku-static pola, które znajduje się w zakresie określonego wątku i domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="419e6-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="419e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="419e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="419e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="419e6-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="419e6-106">podczas Identyfikator klasy zawierającej żądane pole statyczne wątku.</span><span class="sxs-lookup"><span data-stu-id="419e6-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="419e6-107">podczas Token metadanych dla żądanego pola statycznego wątku.</span><span class="sxs-lookup"><span data-stu-id="419e6-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="419e6-108">podczas Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="419e6-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="419e6-109">podczas Identyfikator wątku, który jest zakres dla żądanego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="419e6-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="419e6-110">określoną Wskaźnik do adresu pola statycznego znajdującego się w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="419e6-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="419e6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="419e6-111">Remarks</span></span>  
 <span data-ttu-id="419e6-112">Metoda `GetThreadStaticAddress2` może zwracać jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="419e6-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="419e6-113">CORPROF_E_DATAINCOMPLETE HRESULT, jeśli podane pole statyczne nie ma przypisanego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="419e6-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="419e6-114">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="419e6-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="419e6-115">Te adresy mogą stać się nieprawidłowe po wyrzucaniu elementów bezużytecznych, więc po wybraniu elementów bezużytecznych nie należy zakładać, że są one poprawne.</span><span class="sxs-lookup"><span data-stu-id="419e6-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="419e6-116">Przed ukończeniem konstruktora klasy klasy, `GetThreadStaticAddress2` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, chociaż niektóre pola statyczne mogą już być zainicjowane i główne obiekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="419e6-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="419e6-117">Metoda [ICorProfilerInfo2:: GetThreadStaticAddress —](icorprofilerinfo2-getthreadstaticaddress-method.md) jest podobna do metody `GetThreadStaticAddress2`, ale nie akceptuje argumentu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="419e6-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="419e6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="419e6-118">Requirements</span></span>  
 <span data-ttu-id="419e6-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="419e6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="419e6-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="419e6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="419e6-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="419e6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="419e6-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="419e6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419e6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="419e6-123">See also</span></span>

- [<span data-ttu-id="419e6-124">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="419e6-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="419e6-125">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="419e6-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="419e6-126">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="419e6-126">Profiling</span></span>](index.md)
