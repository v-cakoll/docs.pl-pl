---
title: -filealign (opcje kompilatora C#)
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
ms.openlocfilehash: f3ce1bb864c4cb0b1c330de7d96649f9870231e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328702"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="bc8ce-102">-filealign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bc8ce-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="bc8ce-103">**- Filealign** pozwala określić rozmiar sekcji w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc8ce-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc8ce-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bc8ce-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="bc8ce-106">Wartość, która określa rozmiar sekcji w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="bc8ce-107">Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="bc8ce-108">Te wartości są w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc8ce-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc8ce-109">Remarks</span></span>  
 <span data-ttu-id="bc8ce-110">Każda sekcja będzie wyrównany na granicy, która jest wielokrotnością liczby **- filealign** wartość.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="bc8ce-111">Nie jest stałą domyślnie.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-111">There is no fixed default.</span></span> <span data-ttu-id="bc8ce-112">Jeśli **- filealign** nie zostanie określony, środowisko uruchomieniowe języka wspólnego, wybiera domyślny w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="bc8ce-113">Określając rozmiar sekcji, wpływają na rozmiar pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="bc8ce-114">Modyfikowanie sekcji rozmiaru może być przydatne w przypadku programów, które będą uruchamiane w mniejszych urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="bc8ce-115">Użyj [DUMPBIN](/cpp/build/reference/dumpbin-options) Aby wyświetlić informacje o sekcji w pliku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bc8ce-116">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc8ce-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bc8ce-117">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bc8ce-118">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="bc8ce-119">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="bc8ce-120">Modyfikowanie **wyrównanie pliku** właściwości.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="bc8ce-121">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc8ce-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8ce-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc8ce-122">See also</span></span>

- [<span data-ttu-id="bc8ce-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="bc8ce-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="bc8ce-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bc8ce-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
