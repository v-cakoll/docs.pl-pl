---
title: -pdb (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 108244d7de49c2ff4df1ac7202e77958743b32df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pdb-c-compiler-options"></a><span data-ttu-id="142dc-102">/pdb (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="142dc-102">/pdb (C# Compiler Options)</span></span>
<span data-ttu-id="142dc-103">**/PDB** — opcja kompilatora Określa nazwę i lokalizację pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="142dc-103">The **/pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="142dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="142dc-104">Syntax</span></span>  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="142dc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="142dc-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="142dc-106">Nazwa i lokalizacja pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="142dc-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="142dc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="142dc-107">Remarks</span></span>  
 <span data-ttu-id="142dc-108">Po określeniu [/Debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik PDB w tym samym katalogu, gdy kompilator spowoduje utworzenie pliku wyjściowego (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="142dc-108">When you specify [/debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="142dc-109">**/ PDB** można określić innych niż domyślna nazwa pliku i lokalizację pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="142dc-109">**/pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="142dc-110">Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="142dc-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="142dc-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="142dc-111">Example</span></span>  
 <span data-ttu-id="142dc-112">Kompiluj `t.cs` i Utwórz plik PDB o nazwie tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="142dc-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="142dc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="142dc-113">See Also</span></span>  
 [<span data-ttu-id="142dc-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="142dc-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="142dc-115">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="142dc-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
