---
title: 'Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów'
description: Informacje o usuwaniu zestawu z globalnej pamięci podręcznej zestawów w programie .NET przy użyciu narzędzia globalnej pamięci podręcznej zestawów (Gacutil.exe) lub Instalator Windows.
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
ms.openlocfilehash: e3a596ea6029ded190c33032e96b601de9d4012d
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104773"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="8f21a-103">Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="8f21a-103">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="8f21a-104">Istnieją dwa sposoby usuwania zestawu z globalnej pamięci podręcznej zestawów (GAC):</span><span class="sxs-lookup"><span data-stu-id="8f21a-104">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="8f21a-105">Za pomocą [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8f21a-105">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="8f21a-106">Za pomocą tej opcji można odinstalować zestawy, które zostały umieszczone w pamięci GAC podczas tworzenia i testowania.</span><span class="sxs-lookup"><span data-stu-id="8f21a-106">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="8f21a-107">Za pomocą [Instalator Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="8f21a-107">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="8f21a-108">Tej opcji należy używać do odinstalowywania zestawów podczas testowania pakietów instalacyjnych i systemów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="8f21a-108">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="8f21a-109">Usuwanie zestawu z Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="8f21a-109">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="8f21a-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="8f21a-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="8f21a-111">**Gacutil – u**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="8f21a-111">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="8f21a-112">W tym poleceniu *Nazwa zestawu* to nazwa zestawu, który ma zostać usunięty z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8f21a-112">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="8f21a-113">Nie należy używać Gacutil.exe do usuwania zestawów w systemach produkcyjnych ze względu na możliwość, że zestaw nadal może być wymagany przez niektóre aplikacje.</span><span class="sxs-lookup"><span data-stu-id="8f21a-113">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="8f21a-114">Zamiast tego należy użyć Instalator Windows, która zachowuje liczbę odwołań dla każdego zestawu instalowanego w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="8f21a-114">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="8f21a-115">Poniższy przykład usuwa zestaw o nazwie `hello.dll` z globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="8f21a-115">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="8f21a-116">Usuwanie zestawu z Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="8f21a-116">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="8f21a-117">W aplikacji **programy i funkcje** w **Panelu sterowania**wybierz aplikację, którą chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="8f21a-117">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="8f21a-118">Jeśli pakiet instalacyjny zawiera zestawy w pamięci podręcznej GAC, Instalator Windows usunie je, jeśli nie są używane przez inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f21a-118">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="8f21a-119">Instalator Windows utrzymuje liczbę odwołań dla zestawów zainstalowanych w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="8f21a-119">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="8f21a-120">Zestaw jest usuwany z pamięci GAC tylko wtedy, gdy jego licznik odwołań osiągnie wartość zero, co oznacza, że nie jest używany przez żadną aplikację zainstalowaną przez pakiet Instalator Windows.</span><span class="sxs-lookup"><span data-stu-id="8f21a-120">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f21a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f21a-121">See also</span></span>

- [<span data-ttu-id="8f21a-122">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="8f21a-122">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="8f21a-123">Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="8f21a-123">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="8f21a-124">Gacutil.exe (Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="8f21a-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
