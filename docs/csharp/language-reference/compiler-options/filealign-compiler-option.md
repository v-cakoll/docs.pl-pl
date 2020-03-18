---
title: -filealign (Opcje kompilatora C#)
ms.date: 07/20/2015
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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603009"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="8596f-102">-filealign (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="8596f-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="8596f-103">Opcja **-filealign** umożliwia określenie rozmiaru sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="8596f-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8596f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8596f-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="8596f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8596f-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="8596f-106">Wartość określająca rozmiar sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="8596f-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="8596f-107">Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192.</span><span class="sxs-lookup"><span data-stu-id="8596f-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="8596f-108">Wartości te znajdują się w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8596f-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8596f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8596f-109">Remarks</span></span>  
 <span data-ttu-id="8596f-110">Każda sekcja zostanie wyrównana na granicy, która jest wielokrotnością wartości **-filealign.**</span><span class="sxs-lookup"><span data-stu-id="8596f-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="8596f-111">Nie ma stałej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="8596f-111">There is no fixed default.</span></span> <span data-ttu-id="8596f-112">Jeśli **-filealign** nie jest określony, czas wykonywania języka wspólnego wybiera domyślne w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8596f-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="8596f-113">Określając rozmiar sekcji, można mieć wpływ na rozmiar pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="8596f-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="8596f-114">Modyfikowanie rozmiaru sekcji może być przydatne w przypadku programów, które będą uruchamiane na mniejszych urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="8596f-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="8596f-115">Użyj [DUMPBIN,](/cpp/build/reference/dumpbin-options) aby wyświetlić informacje o sekcjach w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="8596f-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8596f-116">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8596f-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="8596f-117">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="8596f-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="8596f-118">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="8596f-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="8596f-119">Kliknij przycisk **Zaawansowane.**</span><span class="sxs-lookup"><span data-stu-id="8596f-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="8596f-120">Zmodyfikuj właściwość **Wyrównanie plików.**</span><span class="sxs-lookup"><span data-stu-id="8596f-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="8596f-121">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="8596f-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8596f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8596f-122">See also</span></span>

- [<span data-ttu-id="8596f-123">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="8596f-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8596f-124">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="8596f-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
