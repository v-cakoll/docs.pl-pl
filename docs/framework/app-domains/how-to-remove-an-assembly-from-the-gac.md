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
ms.openlocfilehash: 6f3f5d6ae577195987dfcf2d8020e591217b480d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503000"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="3c120-102">Porady: usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="3c120-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="3c120-103">Istnieją dwa sposoby, aby usunąć zestaw z globalnej pamięci podręcznej zestawów (GAC):</span><span class="sxs-lookup"><span data-stu-id="3c120-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="3c120-104">Za pomocą [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="3c120-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="3c120-105">Ta opcja służy do odinstalowania zestawów, które zostały umieszczone w pamięci podręcznej GAC, podczas opracowywania i testowania.</span><span class="sxs-lookup"><span data-stu-id="3c120-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="3c120-106">Za pomocą [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="3c120-106">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="3c120-107">Tej opcji należy używać do odinstalowania zestawów podczas testowania pakietów instalacyjnych, a dla systemów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="3c120-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="3c120-108">Usuwanie zestawu z Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="3c120-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="3c120-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="3c120-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="3c120-110">**Gacutil – u** \< *nazwy zestawu*></span><span class="sxs-lookup"><span data-stu-id="3c120-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="3c120-111">W tym poleceniu *nazwy zestawu* to nazwa zestawu, aby usunąć z globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3c120-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="3c120-112">Nie należy używać Gacutil.exe można usunąć zestawów na systemy produkcyjne ze względu na możliwość, że zestaw nadal może być wymagane przez niektóre aplikacje.</span><span class="sxs-lookup"><span data-stu-id="3c120-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="3c120-113">Zamiast tego należy użyć Instalatora Windows, który przechowuje licznik odwołań dla każdego zestawu, który instaluje go w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="3c120-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="3c120-114">W następującym przykładzie usunięto zestaw o nazwie `hello.dll` z globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3c120-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="3c120-115">Usuwanie zestawu za pomocą Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="3c120-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="3c120-116">Z **programy i funkcje** aplikacji w **Panelu sterowania**, wybierz aplikację, która ma zostać odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="3c120-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="3c120-117">Jeśli pakiet instalacyjny umieszczone zestawów w pamięci podręcznej GAC, Instalator Windows spowoduje usunięcie ich, jeśli nie są one używane przez inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="3c120-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c120-118">Instalator Windows przechowuje licznik odwołań do zestawów zainstalowane w GAC.</span><span class="sxs-lookup"><span data-stu-id="3c120-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="3c120-119">Zestaw zostanie usunięty z pamięci podręcznej GAC, tylko wtedy, gdy jego licznik odwołań osiągnie zero, co oznacza, że nie jest używany przez dowolną aplikację, instalowane przez pakiet Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="3c120-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c120-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c120-120">See Also</span></span>  
 [<span data-ttu-id="3c120-121">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="3c120-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="3c120-122">Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="3c120-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="3c120-123">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="3c120-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
