---
title: -nowarn (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606617"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="6a8cf-102">-nowarn (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="6a8cf-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="6a8cf-103">Opcja **-nowarn** pozwala pominąć kompilator z wyświetlania jednego lub kilku ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="6a8cf-104">Oddziel wiele numerów ostrzeżeń przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8cf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a8cf-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6a8cf-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6a8cf-106">Arguments</span></span>  
 <span data-ttu-id="6a8cf-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="6a8cf-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="6a8cf-108">Liczba ostrzeżeń, które kompilator ma pominąć.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a8cf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a8cf-109">Remarks</span></span>  
 <span data-ttu-id="6a8cf-110">Należy określić tylko liczbowe części identyfikatora ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="6a8cf-111">Na przykład jeśli chcesz pominąć CS0028, możesz określić `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="6a8cf-112">Kompilator zignoruje w sposób cichy odpowiednie numery `-nowarn` ostrzeżeń, które były prawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="6a8cf-113">Na przykład CS0679 był prawidłowy w kompilatorze w Visual Studio .NET 2002, ale został następnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="6a8cf-114">Następujące ostrzeżenia nie mogą być pomijane przez `-nowarn` opcję:</span><span class="sxs-lookup"><span data-stu-id="6a8cf-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="6a8cf-115">Ostrzeżenie kompilatora (poziom 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="6a8cf-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="6a8cf-116">Ostrzeżenie kompilatora (poziom 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="6a8cf-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="6a8cf-117">Ostrzeżenie kompilatora (poziom 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="6a8cf-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6a8cf-118">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6a8cf-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6a8cf-119">Otwórz stronę **Właściwości** dla projektu.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="6a8cf-120">Aby uzyskać szczegółowe informacje, zobacz [stronę Kompilacja, ProjektantC#projektu ()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="6a8cf-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="6a8cf-121">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="6a8cf-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6a8cf-122">Zmodyfikuj właściwość **Pomijaj ostrzeżenia** .</span><span class="sxs-lookup"><span data-stu-id="6a8cf-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="6a8cf-123">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8cf-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a8cf-124">See also</span></span>

- [<span data-ttu-id="6a8cf-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="6a8cf-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6a8cf-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6a8cf-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="6a8cf-127">Błędy kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="6a8cf-127">C# Compiler Errors</span></span>](../compiler-messages/index.md)
