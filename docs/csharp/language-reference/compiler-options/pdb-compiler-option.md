---
title: -pdb (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 9f8158ec0d8de2b9249c4f69830c37480c34b390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217431"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="a5206-102">-pdb (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a5206-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="a5206-103">**- Pdb** — opcja kompilatora Określa nazwę i lokalizację pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="a5206-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5206-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5206-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5206-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a5206-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a5206-106">Nazwa i lokalizacja pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="a5206-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5206-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5206-107">Remarks</span></span>  
 <span data-ttu-id="a5206-108">Po określeniu [-debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik PDB w tym samym katalogu, gdy kompilator spowoduje utworzenie pliku wyjściowego (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a5206-108">When you specify [-debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="a5206-109">**-pdb** pozwala określić nazwę pliku innych niż domyślne i lokalizację pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="a5206-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="a5206-110">Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="a5206-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5206-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5206-111">Example</span></span>  
 <span data-ttu-id="a5206-112">Kompiluj `t.cs` i Utwórz plik PDB o nazwie tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="a5206-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5206-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5206-113">See Also</span></span>  
 [<span data-ttu-id="a5206-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a5206-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="a5206-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a5206-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
