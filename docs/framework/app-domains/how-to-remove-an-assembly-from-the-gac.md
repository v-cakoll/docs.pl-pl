---
title: 'Porady: usuwanie zestawu z globalnej pamięci podręcznej zestawów'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="7eba8-102">Porady: usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="7eba8-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="7eba8-103">Istnieją dwa sposoby usuwanie zestawu z globalnej pamięci podręcznej zestawów (GAC):</span><span class="sxs-lookup"><span data-stu-id="7eba8-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="7eba8-104">Za pomocą [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="7eba8-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="7eba8-105">Ta opcja umożliwia odinstalowanie zestawy, które zostały umieszczone w pamięci GAC podczas projektowania i testowania.</span><span class="sxs-lookup"><span data-stu-id="7eba8-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="7eba8-106">Za pomocą [Instalatora Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="7eba8-106">By using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span> <span data-ttu-id="7eba8-107">Tej opcji należy używać do odinstalowania zestawy podczas testowania pakietów instalacyjnych, a dla systemów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="7eba8-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="7eba8-108">Usuwanie zestawu z Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="7eba8-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="7eba8-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7eba8-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="7eba8-110">**Gacutil – u** \< *nazwy zestawu*></span><span class="sxs-lookup"><span data-stu-id="7eba8-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="7eba8-111">W tym poleceniu *nazwy zestawu* jest nazwą zestawu, aby usunąć z pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="7eba8-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="7eba8-112">Nie należy używać Gacutil.exe można usunąć zestawów w systemach produkcyjnych z powodu możliwości zestawu nadal mogą być wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7eba8-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="7eba8-113">Zamiast tego należy użyć Instalatora systemu Windows, który obsługuje liczba odwołań dla każdego zestawu, który instaluje go w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="7eba8-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="7eba8-114">Poniższy przykład umożliwia usunięcie zestawu o nazwie `hello.dll` z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7eba8-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="7eba8-115">Usuwanie zestawu z Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="7eba8-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="7eba8-116">Z **programy i funkcje** aplikacji w **Panelu sterowania**, wybierz aplikację, którą chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="7eba8-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="7eba8-117">Jeśli pakiet instalacyjny zestawy są umieszczane w pamięci GAC, Instalator systemu Windows będzie je usunąć, jeśli nie są używane przez inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="7eba8-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7eba8-118">Instalator systemu Windows obsługuje liczba odwołań dla zestawów zainstalowanych w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="7eba8-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="7eba8-119">Zestaw zostanie usunięty z pamięci podręcznej GAC tylko wtedy, gdy jego liczebności referencyjnej osiągnie zero, co oznacza, że nie jest używany przez wszelkie aplikacje zainstalowane przez pakiet Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="7eba8-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eba8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7eba8-120">See Also</span></span>  
 [<span data-ttu-id="7eba8-121">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="7eba8-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="7eba8-122">Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="7eba8-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="7eba8-123">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="7eba8-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
