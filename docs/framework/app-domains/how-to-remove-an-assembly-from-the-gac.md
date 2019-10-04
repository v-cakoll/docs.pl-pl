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
ms.openlocfilehash: 7a085ff6955f706bcd90f895c42e6405a28d408a
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834039"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="961c1-102">Porady: usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="961c1-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="961c1-103">Istnieją dwa sposoby usuwania zestawu z globalnej pamięci podręcznej zestawów (GAC):</span><span class="sxs-lookup"><span data-stu-id="961c1-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="961c1-104">Za pomocą [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="961c1-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="961c1-105">Za pomocą tej opcji można odinstalować zestawy, które zostały umieszczone w pamięci GAC podczas tworzenia i testowania.</span><span class="sxs-lookup"><span data-stu-id="961c1-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="961c1-106">Za pomocą [Instalator Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="961c1-106">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="961c1-107">Tej opcji należy używać do odinstalowywania zestawów podczas testowania pakietów instalacyjnych i systemów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="961c1-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="961c1-108">Usuwanie zestawu za pomocą gacutil. exe</span><span class="sxs-lookup"><span data-stu-id="961c1-108">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="961c1-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="961c1-109">At the command prompt, type the following command:</span></span>

<span data-ttu-id="961c1-110">**Gacutil – u** \<*Nazwa zestawu*></span><span class="sxs-lookup"><span data-stu-id="961c1-110">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="961c1-111">W tym poleceniu *Nazwa zestawu* to nazwa zestawu, który ma zostać usunięty z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="961c1-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="961c1-112">Nie należy używać programu Gacutil. exe do usuwania zestawów w systemach produkcyjnych ze względu na możliwość, że zestaw nadal może być wymagany przez niektóre aplikacje.</span><span class="sxs-lookup"><span data-stu-id="961c1-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="961c1-113">Zamiast tego należy użyć Instalator Windows, która zachowuje liczbę odwołań dla każdego zestawu instalowanego w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="961c1-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="961c1-114">Poniższy przykład usuwa zestaw o nazwie `hello.dll` z globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="961c1-114">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="961c1-115">Usuwanie zestawu z Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="961c1-115">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="961c1-116">W aplikacji **programy i funkcje** w **Panelu sterowania**wybierz aplikację, którą chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="961c1-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="961c1-117">Jeśli pakiet instalacyjny zawiera zestawy w pamięci podręcznej GAC, Instalator Windows usunie je, jeśli nie są używane przez inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="961c1-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="961c1-118">Instalator Windows utrzymuje liczbę odwołań dla zestawów zainstalowanych w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="961c1-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="961c1-119">Zestaw jest usuwany z pamięci GAC tylko wtedy, gdy jego licznik odwołań osiągnie wartość zero, co oznacza, że nie jest używany przez żadną aplikację zainstalowaną przez pakiet Instalator Windows.</span><span class="sxs-lookup"><span data-stu-id="961c1-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="961c1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="961c1-120">See also</span></span>

- [<span data-ttu-id="961c1-121">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="961c1-121">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="961c1-122">Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="961c1-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="961c1-123">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="961c1-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
