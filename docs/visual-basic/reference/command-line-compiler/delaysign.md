---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: c9bb302e2b34ebe1f51cf39bb3db1094d420d7f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408702"
---
# <a name="-delaysign"></a><span data-ttu-id="c666d-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="c666d-102">-delaysign</span></span>

<span data-ttu-id="c666d-103">Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.</span><span class="sxs-lookup"><span data-stu-id="c666d-103">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="c666d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c666d-104">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="c666d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c666d-105">Arguments</span></span>

<span data-ttu-id="c666d-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="c666d-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="c666d-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c666d-107">Optional.</span></span> <span data-ttu-id="c666d-108">Użyj `-delaysign-` , jeśli chcesz użyć w pełni podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c666d-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="c666d-109">Użyj, `-delaysign+` Jeśli chcesz umieścić klucz publiczny w zestawie i zarezerwować miejsce dla podpisanej wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c666d-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="c666d-110">Wartość domyślna to `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="c666d-110">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c666d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c666d-111">Remarks</span></span>

<span data-ttu-id="c666d-112">`-delaysign`Opcja nie ma żadnego efektu, chyba że zostanie użyta z [-KeyFile](keyfile.md) lub [-containerer](keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="c666d-112">The `-delaysign` option has no effect unless used with [-keyfile](keyfile.md) or [-keycontainer](keycontainer.md).</span></span>

<span data-ttu-id="c666d-113">Po zażądaniu w pełni podpisanego zestawu, kompilator skrótów pliku, który zawiera manifest (metadane zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="c666d-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="c666d-114">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="c666d-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="c666d-115">Gdy zestaw jest podpisany z opóźnieniem, kompilator nie oblicza i nie przechowuje podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.</span><span class="sxs-lookup"><span data-stu-id="c666d-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="c666d-116">Na przykład przy użyciu `-delaysign+` , deweloper w organizacji może rozpowszechniać niepodpisane wersje testów zestawu, które testerzy mogą zarejestrować w globalnej pamięci podręcznej zestawów i używać.</span><span class="sxs-lookup"><span data-stu-id="c666d-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="c666d-117">Po zakończeniu pracy z zestawem osoba odpowiedzialna za klucz prywatny organizacji może w pełni podpisać zestaw.</span><span class="sxs-lookup"><span data-stu-id="c666d-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="c666d-118">Ta compartmentalization chroni klucz prywatny organizacji przed ujawnieniem, jednocześnie pozwalając wszystkim deweloperom na współdziałanie z zestawami.</span><span class="sxs-lookup"><span data-stu-id="c666d-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="c666d-119">Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="c666d-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="c666d-120">Aby ustawić-delaysign w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c666d-120">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="c666d-121">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c666d-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c666d-122">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c666d-122">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="c666d-123">Kliknij kartę **podpisywanie** .</span><span class="sxs-lookup"><span data-stu-id="c666d-123">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="c666d-124">Ustaw wartość w polu **Opóźnij tylko znak** .</span><span class="sxs-lookup"><span data-stu-id="c666d-124">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="c666d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c666d-125">See also</span></span>

- [<span data-ttu-id="c666d-126">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c666d-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c666d-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="c666d-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="c666d-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="c666d-128">-keycontainer</span></span>](keycontainer.md)
- [<span data-ttu-id="c666d-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c666d-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
