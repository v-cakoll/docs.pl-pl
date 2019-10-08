---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 66edc45c622b78187469ccc0631beb53b68049b0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002298"
---
# <a name="-delaysign"></a><span data-ttu-id="c1a15-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="c1a15-102">-delaysign</span></span>
<span data-ttu-id="c1a15-103">Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.</span><span class="sxs-lookup"><span data-stu-id="c1a15-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1a15-104">Syntax</span></span>  
  
```console  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1a15-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c1a15-105">Arguments</span></span>  
 <span data-ttu-id="c1a15-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c1a15-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c1a15-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c1a15-107">Optional.</span></span> <span data-ttu-id="c1a15-108">Użyj `-delaysign-`, jeśli chcesz użyć w pełni podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1a15-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="c1a15-109">Użyj `-delaysign+`, jeśli chcesz umieścić klucz publiczny w zestawie i zarezerwować miejsce dla podpisanej wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c1a15-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="c1a15-110">Wartość domyślna to `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="c1a15-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1a15-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1a15-111">Remarks</span></span>  
 <span data-ttu-id="c1a15-112">Opcja `-delaysign` nie ma żadnego efektu, chyba że zostanie użyta z opcją [-KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [-containerer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="c1a15-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="c1a15-113">Po zażądaniu w pełni podpisanego zestawu, kompilator skrótów pliku, który zawiera manifest (metadane zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="c1a15-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="c1a15-114">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="c1a15-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="c1a15-115">Gdy zestaw jest podpisany z opóźnieniem, kompilator nie oblicza i nie przechowuje podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.</span><span class="sxs-lookup"><span data-stu-id="c1a15-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="c1a15-116">Na przykład przy użyciu `-delaysign+` deweloper w organizacji może rozpowszechniać niepodpisane wersje testów zestawu, które testerzy mogą zarejestrować w globalnej pamięci podręcznej zestawów i używać.</span><span class="sxs-lookup"><span data-stu-id="c1a15-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="c1a15-117">Po zakończeniu pracy z zestawem osoba odpowiedzialna za klucz prywatny organizacji może w pełni podpisać zestaw.</span><span class="sxs-lookup"><span data-stu-id="c1a15-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="c1a15-118">Ta compartmentalization chroni klucz prywatny organizacji przed ujawnieniem, jednocześnie pozwalając wszystkim deweloperom na współdziałanie z zestawami.</span><span class="sxs-lookup"><span data-stu-id="c1a15-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="c1a15-119">Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1a15-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="c1a15-120">Aby ustawić-delaysign w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1a15-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="c1a15-121">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c1a15-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c1a15-122">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c1a15-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="c1a15-123">Kliknij kartę **podpisywanie** .</span><span class="sxs-lookup"><span data-stu-id="c1a15-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="c1a15-124">Ustaw wartość w polu **Opóźnij tylko znak** .</span><span class="sxs-lookup"><span data-stu-id="c1a15-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a15-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1a15-125">See also</span></span>

- [<span data-ttu-id="c1a15-126">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1a15-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c1a15-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="c1a15-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="c1a15-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="c1a15-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="c1a15-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c1a15-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
