---
title: -filealign (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f00db0cfd191de060b67aee4618d99740cb81248
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="fc3c4-102">-filealign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="fc3c4-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="fc3c4-103">**- Filealign** pozwala określić rozmiar sekcji w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc3c4-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc3c4-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fc3c4-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="fc3c4-106">Wartość określająca rozmiar sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="fc3c4-107">Prawidłowe wartości to 512, 1024, 2048, 4096 do 8192.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="fc3c4-108">Te wartości są w bajtach.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc3c4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc3c4-109">Remarks</span></span>  
 <span data-ttu-id="fc3c4-110">Każda sekcja będzie wyrównany na granicy, która jest wielokrotnością liczby **- filealign** wartość.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="fc3c4-111">Nie jest domyślnie stałym.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-111">There is no fixed default.</span></span> <span data-ttu-id="fc3c4-112">Jeśli **- filealign** nie zostanie określony, środowisko uruchomieniowe języka wspólnego wybiera domyślny, w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="fc3c4-113">Określając rozmiar sekcji wpływa na rozmiar pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="fc3c4-114">Modyfikowanie rozmiar sekcji mogą być przydatne dla programów uruchamianych na mniejsze urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="fc3c4-115">Użyj [DUMPBIN](/cpp/build/reference/dumpbin-options) Aby wyświetlić informacje o sekcji w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fc3c4-116">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc3c4-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="fc3c4-117">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="fc3c4-118">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="fc3c4-119">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="fc3c4-120">Modyfikowanie **wyrównanie pliku** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="fc3c4-121">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc3c4-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3c4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc3c4-122">See Also</span></span>  
 [<span data-ttu-id="fc3c4-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="fc3c4-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="fc3c4-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fc3c4-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
