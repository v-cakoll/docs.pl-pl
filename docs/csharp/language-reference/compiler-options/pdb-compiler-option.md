---
title: -pdb (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602576"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="c3989-102">-pdb (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c3989-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="c3989-103">Opcja kompilatora **-pdb** określa nazwę i lokalizację pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="c3989-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3989-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3989-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3989-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c3989-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c3989-106">Nazwa i lokalizacja pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="c3989-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3989-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3989-107">Remarks</span></span>  
 <span data-ttu-id="c3989-108">Po [określeniu -debug (C# Opcje kompilatora),](./debug-compiler-option.md)kompilator utworzy plik .pdb w tym samym katalogu, w którym kompilator utworzy plik wyjściowy (.exe lub .dll) o nazwie pliku, która jest taka sama jak nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c3989-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="c3989-109">**-pdb** umożliwia określenie niedomyślnej nazwy pliku i lokalizacji pliku pdb.</span><span class="sxs-lookup"><span data-stu-id="c3989-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="c3989-110">Nie można ustawić tej opcji kompilatora w środowisku programistycznym programu Visual Studio ani nie można jej programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="c3989-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3989-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3989-111">Example</span></span>  
 <span data-ttu-id="c3989-112">Skompiluj `t.cs` i utwórz plik pdb o nazwie tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="c3989-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3989-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3989-113">See also</span></span>

- [<span data-ttu-id="c3989-114">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="c3989-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c3989-115">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="c3989-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
