---
title: -pdb (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7528283765c2b6f4a9d5e84015526a95938a6281
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="c709e-102">-pdb (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c709e-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="c709e-103">**- Pdb** — opcja kompilatora Określa nazwę i lokalizację pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="c709e-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c709e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c709e-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c709e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c709e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c709e-106">Nazwa i lokalizacja pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="c709e-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c709e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c709e-107">Remarks</span></span>  
 <span data-ttu-id="c709e-108">Po określeniu [-debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik PDB w tym samym katalogu, gdy kompilator spowoduje utworzenie pliku wyjściowego (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c709e-108">When you specify [-debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="c709e-109">**-pdb** pozwala określić nazwę pliku innych niż domyślne i lokalizację pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="c709e-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="c709e-110">Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="c709e-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c709e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c709e-111">Example</span></span>  
 <span data-ttu-id="c709e-112">Kompiluj `t.cs` i Utwórz plik PDB o nazwie tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="c709e-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c709e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c709e-113">See Also</span></span>  
 [<span data-ttu-id="c709e-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c709e-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="c709e-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c709e-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
