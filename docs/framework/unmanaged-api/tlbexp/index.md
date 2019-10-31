---
title: Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104126"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="87f81-102">Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="87f81-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="87f81-103">[Narzędzie eksportu biblioteki typów](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe) ładuje bibliotekę dołączaną dynamicznie o nazwie TlbRef. dll.</span><span class="sxs-lookup"><span data-stu-id="87f81-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="87f81-104">Ta biblioteka DLL zawiera dwie funkcje pomocnika i interfejs, którego używa narzędzie eksportu w procesie konwersji zestawu na typ biblioteki.</span><span class="sxs-lookup"><span data-stu-id="87f81-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87f81-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="87f81-105">In This Section</span></span>  
 [<span data-ttu-id="87f81-106">GetTypeLibInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="87f81-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="87f81-107">Zapewnia lokalizację i informacje o systemie operacyjnym dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="87f81-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="87f81-108">LoadTypeLibWithResolver, funkcja</span><span class="sxs-lookup"><span data-stu-id="87f81-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="87f81-109">Ładuje bibliotekę typów przy użyciu implementacji [interfejsu ITypeLibResolver](itypelibresolver-interface.md) , aby rozwiązać wszelkie odwołania do bibliotek typów.</span><span class="sxs-lookup"><span data-stu-id="87f81-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="87f81-110">ITypeLibResolver, interfejs</span><span class="sxs-lookup"><span data-stu-id="87f81-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="87f81-111">Udostępnia [metodę ResolveTypeLib —](resolvetypelib-method.md), która zwraca w pełni kwalifikowaną ścieżkę do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="87f81-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
