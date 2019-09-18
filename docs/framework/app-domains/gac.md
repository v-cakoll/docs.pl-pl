---
title: Global Assembly Cache
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a2ac0c7fb5f89c7d6b9daba8da7b37d1135acb6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053185"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="93b68-102">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="93b68-102">Global Assembly Cache</span></span>
<span data-ttu-id="93b68-103">Każdy komputer, na którym jest zainstalowany środowisko uruchomieniowe języka wspólnego, ma pamięć podręczną kodu całego komputera o nazwie globalna pamięć podręczna zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-103">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="93b68-104">Globalna pamięć podręczna zestawów przechowuje zestawy specjalnie wyznaczonych do współużytkowania przez kilka aplikacji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="93b68-104">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="93b68-105">Zestawy należy udostępniać, instalując je w globalnej pamięci podręcznej zestawów tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="93b68-105">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="93b68-106">Ogólnie rzecz biorąc, Zachowaj zależności zestawów jako prywatne i lokalizowanie zestawów w katalogu aplikacji, o ile udostępnianie zestawu nie jest jawnie wymagane.</span><span class="sxs-lookup"><span data-stu-id="93b68-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="93b68-107">Ponadto nie trzeba instalować zestawów w globalnej pamięci podręcznej zestawów, aby umożliwić ich dostęp do międzyoperacyjności modelu COM lub kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="93b68-107">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93b68-108">Istnieją scenariusze, w których jawnie nie trzeba instalować zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-108">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="93b68-109">W przypadku umieszczenia jednego z zestawów, które tworzą aplikację w globalnej pamięci podręcznej zestawów, nie można już replikować ani instalować aplikacji przy użyciu polecenia **xcopy** w celu skopiowania katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93b68-109">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="93b68-110">Należy również przenieść zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-110">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="93b68-111">Istnieją dwa sposoby wdrożenia zestawu w globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="93b68-111">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="93b68-112">Użyj Instalatora zaprojektowanego do pracy z globalną pamięcią podręczną zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-112">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="93b68-113">Jest to preferowana opcja instalowania zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-113">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="93b68-114">Użyj narzędzia deweloperskiego o nazwie [globalne narzędzie pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md)dostarczonego przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="93b68-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="93b68-115">W scenariuszach wdrażania należy użyć Instalator Windows, aby zainstalować zestawy w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-115">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="93b68-116">Narzędzia globalnej pamięci podręcznej zestawów można używać tylko w scenariuszach deweloperskich, ponieważ nie zapewnia to zliczania odwołań do zestawów i innych funkcji dostępnych podczas korzystania z Instalator Windows.</span><span class="sxs-lookup"><span data-stu-id="93b68-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="93b68-117">Począwszy od .NET Framework 4, domyślną lokalizacją globalnej pamięci podręcznej zestawów jest **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="93b68-117">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="93b68-118">We wcześniejszych wersjach .NET Framework domyślną lokalizacją jest **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="93b68-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="93b68-119">Administratorzy często chronią katalog główny_katalog_systemowy przy użyciu listy kontroli dostępu (ACL) w celu kontrolowania dostępu do zapisu i wykonywania.</span><span class="sxs-lookup"><span data-stu-id="93b68-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="93b68-120">Ponieważ globalna pamięć podręczna zestawów jest instalowana w podkatalogu katalogu główny_katalog_systemowy, dziedziczy listę ACL tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="93b68-120">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="93b68-121">Zaleca się, aby tylko użytkownicy z uprawnieniami administratora mogli usuwać pliki z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="93b68-121">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="93b68-122">Zestawy wdrożone w globalnej pamięci podręcznej zestawów muszą mieć silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="93b68-122">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="93b68-123">Po dodaniu zestawu do globalnej pamięci podręcznej zestawów sprawdzane są wszystkie pliki wchodzące w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="93b68-123">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="93b68-124">Pamięć podręczna wykonuje te operacje sprawdzania integralności, aby upewnić się, że zestaw nie został naruszony, na przykład wtedy, gdy plik został zmieniony, ale manifest nie odzwierciedla zmiany.</span><span class="sxs-lookup"><span data-stu-id="93b68-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b68-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93b68-125">See also</span></span>

- [<span data-ttu-id="93b68-126">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="93b68-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="93b68-127">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="93b68-127">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="93b68-128">Zestawy o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="93b68-128">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
