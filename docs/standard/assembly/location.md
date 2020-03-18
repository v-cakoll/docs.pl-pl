---
title: Lokalizacja zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733127"
---
# <a name="assembly-location"></a><span data-ttu-id="69b61-102">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="69b61-102">Assembly location</span></span>
<span data-ttu-id="69b61-103">Lokalizacja zestawu określa, czy czas wykonywania języka wspólnego można zlokalizować, gdy odwołuje się, a także można określić, czy zestaw może być współużytkowany z innymi zestawami.</span><span class="sxs-lookup"><span data-stu-id="69b61-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="69b61-104">Można wdrożyć zestaw w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="69b61-104">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="69b61-105">Katalog lub podkatalogi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69b61-105">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="69b61-106">Jest to najbardziej popularna lokalizacja do wdrażania zestawu.</span><span class="sxs-lookup"><span data-stu-id="69b61-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="69b61-107">Podkatalogi katalogu głównego aplikacji mogą być oparte na języku lub kulturze.</span><span class="sxs-lookup"><span data-stu-id="69b61-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="69b61-108">Jeśli zestaw ma informacje w atrybucie kultury, musi znajdować się w podkatalogu pod katalogiem aplikacji o nazwie tej kultury.</span><span class="sxs-lookup"><span data-stu-id="69b61-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="69b61-109">Globalna pamięć podręczna zestawów.</span><span class="sxs-lookup"><span data-stu-id="69b61-109">The global assembly cache.</span></span>

     <span data-ttu-id="69b61-110">Jest to pamięć podręczna kodu całego komputera, która jest instalowana wszędzie tam, gdzie jest zainstalowany czas wykonywania języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="69b61-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="69b61-111">W większości przypadków, jeśli zamierzasz udostępnić zestaw z wieloma aplikacjami, należy wdrożyć go w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="69b61-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="69b61-112">Na serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="69b61-112">On an HTTP server.</span></span>

     <span data-ttu-id="69b61-113">Zestaw wdrożony na serwerze HTTP musi mieć silną nazwę; wskazywać zestaw w sekcji bazy kodu pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69b61-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="69b61-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69b61-114">See also</span></span>

- [<span data-ttu-id="69b61-115">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="69b61-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="69b61-116">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="69b61-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="69b61-117">Jak program runtime lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="69b61-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
