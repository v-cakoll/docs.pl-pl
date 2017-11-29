---
title: Global Assembly Cache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ca51a06e6e7ec89576facf3a70c789325fd893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="global-assembly-cache"></a><span data-ttu-id="b464d-102">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="b464d-102">Global Assembly Cache</span></span>
<span data-ttu-id="b464d-103">Każdy komputer, na którym zainstalowano środowisko uruchomieniowe języka wspólnego używa pamięci podręcznej kodu dla komputera o nazwie globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b464d-103">Each computer where the common language runtime is installed has a machine-wide code cache called the global assembly cache.</span></span> <span data-ttu-id="b464d-104">Globalna pamięć podręczna zestawów przechowuje zestawy wyznaczonych być współużytkowane przez kilka aplikacji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b464d-104">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="b464d-105">Zestawy powinny współużytkować przez zainstalowanie ich w pamięci podręcznej GAC tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="b464d-105">You should share assemblies by installing them into the global assembly cache only when you need to.</span></span> <span data-ttu-id="b464d-106">Generalnie zachowywać prywatność zestawów i lokalizowanie zestawów w katalogu aplikacji, chyba że jawnie wymagana jest udostępnianie zestawu.</span><span class="sxs-lookup"><span data-stu-id="b464d-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="b464d-107">Ponadto nie jest konieczne zainstalowanie zestawów w globalnej pamięci podręcznej zestawów Aby udostępnić COM interop lub kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b464d-107">In addition, it is not necessary to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b464d-108">Istnieją scenariusze, w którym jawnie nie chcesz instalować zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b464d-108">There are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="b464d-109">Jeśli jeden z zestawów, które tworzą aplikacji w pamięci podręcznej GAC, można już replikacji lub zainstalować aplikację przy użyciu **xcopy** polecenie, aby skopiować z katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b464d-109">If you place one of the assemblies that make up an application in the global assembly cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="b464d-110">Należy przenieść zestawu w globalnej pamięci podręcznej zestawów również.</span><span class="sxs-lookup"><span data-stu-id="b464d-110">You must move the assembly in the global assembly cache as well.</span></span>  
  
 <span data-ttu-id="b464d-111">Istnieją dwa sposoby wdrożenia zestawu w globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="b464d-111">There are two ways to deploy an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="b464d-112">Użyj Instalatora zaprojektowane do pracy z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b464d-112">Use an installer designed to work with the global assembly cache.</span></span> <span data-ttu-id="b464d-113">Jest to preferowaną opcję instalowania zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b464d-113">This is the preferred option for installing assemblies into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="b464d-114">Za pomocą narzędzia Projektant o nazwie [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), podany przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b464d-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b464d-115">W scenariuszach wdrażania za pomocą Instalatora Windows zainstaluj zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b464d-115">In deployment scenarios, use Windows Installer to install assemblies into the global assembly cache.</span></span> <span data-ttu-id="b464d-116">Narzędzie Global Assembly Cache tylko w przypadku scenariuszy programowania, ponieważ nie zawiera on liczenie odwołań zestawu i inne funkcje podany przy wywołaniu metody za pomocą Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="b464d-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="b464d-117">Począwszy od programu .NET Framework 4, jest domyślną lokalizację pamięci podręcznej GAC **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="b464d-117">Starting with the .NET Framework 4, the default location for the global assembly cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="b464d-118">We wcześniejszych wersjach programu .NET Framework, domyślna lokalizacja to **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="b464d-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="b464d-119">Administratorzy często chronią katalog do kontrolowania zapisu i wykonywania dostępu za pomocą listy kontroli dostępu (ACL).</span><span class="sxs-lookup"><span data-stu-id="b464d-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="b464d-120">Ponieważ Globalna pamięć podręczna zestawów jest instalowany w podkatalogu w katalogu systemowym, dziedziczy ACL tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b464d-120">Because the global assembly cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="b464d-121">Zaleca się, że tylko użytkownicy z uprawnieniami administratora można usunąć pliki z pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="b464d-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
 <span data-ttu-id="b464d-122">Zestawy wdrożone w pamięci podręcznej GAC musi mieć silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b464d-122">Assemblies deployed in the global assembly cache must have a strong name.</span></span> <span data-ttu-id="b464d-123">Zestaw został dodany do globalnej pamięci podręcznej zestawów, sprawdzania integralności są wykonywane na wszystkie pliki wchodzące w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="b464d-123">When an assembly is added to the global assembly cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="b464d-124">Pamięć podręczna wykonuje te testy integralności, aby upewnić się, że zestaw nie został zmodyfikowany, na przykład, gdy plik został zmieniony, ale manifest nie odzwierciedla zmiany.</span><span class="sxs-lookup"><span data-stu-id="b464d-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b464d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b464d-125">See Also</span></span>  
 [<span data-ttu-id="b464d-126">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="b464d-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="b464d-127">Praca z zestawami i Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="b464d-127">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="b464d-128">Zestawy o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="b464d-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
