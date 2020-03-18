---
title: -nowarn (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606617"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="ad9d5-102">-nowarn (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="ad9d5-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="ad9d5-103">Opcja **-nowarn** umożliwia wyłączenie kompilatora z wyświetlania co najmniej jednego ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="ad9d5-104">Oddziel wiele numerów ostrzegawczych przecinkiem.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad9d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad9d5-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad9d5-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ad9d5-106">Arguments</span></span>  
 <span data-ttu-id="ad9d5-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="ad9d5-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="ad9d5-108">Liczba (s) ostrzeżenie, które mają kompilator pominąć.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad9d5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad9d5-109">Remarks</span></span>  
 <span data-ttu-id="ad9d5-110">Należy określić tylko numeryczne część identyfikatora ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="ad9d5-111">Na przykład, jeśli chcesz pominąć CS0028, można określić `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="ad9d5-112">Kompilator będzie dyskretnie ignorować numery ostrzeżeń przekazywane do, `-nowarn` które były prawidłowe w poprzednich wersjach, ale które zostały usunięte z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="ad9d5-113">Na przykład CS0679 był prawidłowy w kompilatorze w programie Visual Studio .NET 2002, ale został następnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="ad9d5-114">Opcja ta nie może zostać `-nowarn` wygaszona przez następujące ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="ad9d5-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="ad9d5-115">Ostrzeżenie o kompilatorze (poziom 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="ad9d5-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="ad9d5-116">Ostrzeżenie o kompilatorze (poziom 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="ad9d5-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="ad9d5-117">Ostrzeżenie o kompilatorze (poziom 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="ad9d5-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ad9d5-118">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ad9d5-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ad9d5-119">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="ad9d5-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="ad9d5-120">Aby uzyskać szczegółowe informacje, zobacz [Tworzenie strony, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ad9d5-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="ad9d5-121">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="ad9d5-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ad9d5-122">Zmodyfikuj właściwość **Pomiń ostrzeżenia.**</span><span class="sxs-lookup"><span data-stu-id="ad9d5-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="ad9d5-123">Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="ad9d5-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9d5-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad9d5-124">See also</span></span>

- [<span data-ttu-id="ad9d5-125">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="ad9d5-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ad9d5-126">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="ad9d5-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="ad9d5-127">Błędy kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="ad9d5-127">C# Compiler Errors</span></span>](../compiler-messages/index.md)
